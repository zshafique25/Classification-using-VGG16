# Classification-using-VGG16
1. Change the grid input dimension: The VGG16 was initially trained for color images. Therefore, it needs to receive images with color channels. That is, each pixel of the image will be represented by more than one value. Typically, we use the RGB color system, that is, each pixel of the image is composed of three values. We can therefore say that an image 32 pixels wide and 32 pixels high in the RGB system has a dimensionality of 32x32x3. As the Fashion MNIST images are in grayscale (that is, they only have one color channel and, therefore, each image has a size of 28x28x1), it is necessary to resize the dataset images to 32x32x3, adding another two channels to use the VGG16.
2. Change the output layer: The output layer of the original VGG16 has 1000 neurons, which correspond to the number of classes in the ImageNet dataset. For Fashion MNIST, you need to change the number of neurons in the output layer to 10, which is the number of classes in the dataset. Therefore, it is necessary to replace the VGG16 output layer with a new dense layer with 10 neurons and a softmax activation layer for classification.
3. Tuning the optimizer learning rate: As Fashion MNIST is a simpler dataset compared to ImageNet, it may be necessary to adjust the optimizer learning rate to a lower value in order to avoid overfitting.
## Model Fitting:
This function defines a training procedure for the deep learning model. It takes as input the compiled model, training and testing data, and returns the evaluation score and the training history.
The training procedure involves setting up callbacks, which are functions that can be executed during the training process. In this case, three callbacks are used:
1. EarlyStopping: This stops the training process if the monitored metric (validation loss in this case) does not improve for a certain number of epochs (patience). It helps to prevent overfitting and saves time by stopping the training process early.
2. ModelCheckpoint: This saves the weights of the best-performing model based on the monitored metric (validation loss in this case). This is useful in case the training process is interrupted, as the best weights can be loaded later.
3. ReduceLROnPlateau: This reduces the learning rate when the monitored metric (validation loss in this case) stops improving. This helps to fine-tune the model and avoid getting stuck in local minima.
## Train and Test loss and accuracy graphs:
![image](https://github.com/zshafique25/Classification-using-VGG16/assets/127844420/18f545f6-d363-499d-bf5c-bda924e99d44)![image](https://github.com/zshafique25/Classification-using-VGG16/assets/127844420/73a67e82-4f32-47f7-b47f-5944dda4e1cc)
## Overall Model Accuracy: 93.2%

