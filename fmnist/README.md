# Wasserstein GAN for Fashion MNIST Datasets

### Generative Adversarial Network (GAN)
Generative Adversarial Network (GAN) was first introduced in 2014 by a group of researchers lead by Ian Goodfellow from University of Montreal. GAN is a very interesting idea where it has two competing neural network, Generator (G) and Discriminator (D). Generator takes noise as input and generates samples where Discriminator receive sample from Generator and training data. Discriminator objective is to distinguish corectly between data from generator and training data. In the begining Generator will produce a random noise that doens't look like training sample at all. But over time, Generator will learn to produce more realistic samples. Simultaneously, Discriminator will also learn to get better at distinguishing between generated data from real data. This process will go on with the hope that generated samples will be indistinguishable from real data.

To summarize, GAN consist of two network:

 - A discriminator D receive input from training data and generated data. Its job is to learn how to distinguish between these two input.
 - A generator G generate samples from a random noise Z. Generator objective is to generate sample that is as real as possible it could not  be distinguished by Discriminator.

### Wasserstein GAN
Main problem in GAN is it is very unstable during training. The generator may produce the same output all the time. This scenario are commonly referred as Mode Collapse. In this scenario the generator successfully fool the discriminator but sample generated by generator are not diverse and fails to represent the real data distribution. 

Wasserstein GAN try to deal with the original GAN problem by using the Earth-Mover distance or Wasserstein-1. The Wasserstein-1 has an advantage over Jenson-Shannon divergence where its gradient will not vanish when the generator reaches regions that are defined by the discriminator. As a result, it is possible to train the discriminator in more iteration than the generator without worrying about the balance between generator and discriminator. The model will converge better compare to the original GAN in price of slower training process since more iteration is required on the discriminator side.

#### Run the training process
```sh
python wgan_train.py
```

#### Generate from pre-trained model
```sh
python wgan_generate.py
```

#### Check Tensorboard
```sh
tensorboard --logdir=tensorboard-trained
```
### Training Example
![](https://github.com/kvpratama/gan/blob/master/fmnist/fmnist.gif)

### Generator Loss
![](https://preview.ibb.co/dGCikG/fmnist_gloss.png)
### Discriminator Loss
![](https://preview.ibb.co/iRbXeb/fmnist_dloss.png)
