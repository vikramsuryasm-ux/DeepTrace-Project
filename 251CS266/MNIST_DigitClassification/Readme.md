The model attached has a test accuracy of 99.45% and a training accuracy of 99.6%

The architecture of the model involves multiple Convolution layers of 2 dimensions and a kernel of 3*3 size in the beginning retaining the 2D structure of images and uses ReLU activation function. It later uses batch normalization 2D and Dropout in order to regularize the neural pathways and to prevent overfitting. The two MaxPool layers were added to reduce the compute required since the effects of such pooling are insignificant in datasets such as MNIST.

Lastly, it uses flattening to convert the 2D features to a 1D vector which is then passed through linear layers and activation functions along with normalization to give the final 10 neurons representing the 10 classes of the classification of images.

# Loss Functiion Choice

It uses CrossEntropyLoss because the target labels are processed as raw integers rather than the expanded vectors as in one hot encoding. This function combines LogSoftmax and NLLLoss to give an efficient choice for models such as these avoiding the addition of another layer of transformation at the end allowing us to use the raw logits at the final layer.

# Optimizer Choice

The Adam functiun utilizes the calculation of the values called momentums which result in a maintenance of directional preference based on the previous values of gradients. This helps it to accelerate through the small flatter regions with higher learning rate and automatically reduce rate when encountering wild oscillating updates.

# Scheduler Choice

This helps achieve high accuracies by appropriately checking for test accuracy at the end of each epoch, and then update the learning rate as mentioned in the factor parameter when the number of epochs that has stalled or decreased from previous epochs exceeds the patience value. ZUpon trying a few values, the used parameters proved to be more efficient.