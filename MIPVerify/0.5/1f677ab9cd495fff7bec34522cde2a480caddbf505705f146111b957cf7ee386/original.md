```julia
read_datasets(name)

```

Makes popular machine learning datasets available as a `NamedTrainTestDataset`.

# Arguments

  * `name::String`: name of machine learning dataset. Options:

      * `MNIST`: [The MNIST Database of handwritten digits](http://yann.lecun.com/exdb/mnist/). Pixel values in original dataset are provided as uint8 (0 to 255), but are scaled to range from 0 to 1 here.
      * `CIFAR10`: [Labelled subset in 10 classes of 80 million tiny images dataset](https://www.cs.toronto.edu/~kriz/cifar.html). Pixel values in original dataset are provided as uint8 (0 to 255), but are scaled to range from 0 to 1 here.
