```
traindbm!(dbm, x; ...)
```

Trains the `dbm` (a `BasicDBM` or a more general `MultimodalDBM`) using the learning procedure for a general Boltzmann Machine with the training data set `x`. A learning step consists of mean-field inference (positive phase), stochastic approximation by Gibbs Sampling (negative phase) and the parameter updates.

# Optional keyword arguments (ordered by importance):

  * `epoch`: number of training epochs
  * `learningrate`/`learningrates`: a vector of learning rates for each epoch to  update the weights and biases. The learning rates should decrease with the  epochs, e. g. with the factor `a / (b + epoch)`. If only one value is given as  `learningrate`, `a` and `b` are 11.0 and 10.0, respectively.
  * `batchsize`: number of samples in mini-batches.  No mini-batches are used by default, which means that  the complete data set is used for calculating the gradient in each epoch.
  * `nparticles`: number of particles used for sampling, default 100
  * `monitoring`: A function that is executed after each training epoch.  It has to accept the trained DBM and the current epoch as arguments.
