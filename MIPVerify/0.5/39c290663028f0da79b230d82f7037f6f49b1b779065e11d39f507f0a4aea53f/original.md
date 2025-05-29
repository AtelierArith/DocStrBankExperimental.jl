```julia
frac_correct(nn, dataset, num_samples)

```

Returns the fraction of items the neural network correctly classifies of the first `num_samples` of the provided `dataset`. If there are fewer than `num_samples` items, we use all of the available samples.

# Named Arguments:

  * `nn::NeuralNet`: The parameters of the neural network.
  * `dataset::LabelledDataset`:
  * `num_samples::Integer`: Number of samples to use.
