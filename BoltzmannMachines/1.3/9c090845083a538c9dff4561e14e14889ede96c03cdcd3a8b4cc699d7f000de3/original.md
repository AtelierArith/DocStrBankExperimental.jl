```
fitrbm(x; ...)
```

Fits an RBM model to the data set `x`, using Stochastic Gradient Descent (SGD) with Contrastive Divergence (CD), and returns it.

# Optional keyword arguments (ordered by importance):

  * `rbmtype`: the type of the RBM that is to be trained  This must be a subtype of `AbstractRBM` and defaults to `BernoulliRBM`.
  * `nhidden`: number of hidden units for the returned RBM
  * `epochs`: number of training epochs
  * `learningrate`/`learningrates`: The learning rate for the weights and biases  can be specified as single value, used throughout all epochs, or as a vector  of `learningrates` that contains a value for each epoch. Defaults to 0.005.
  * `batchsize`: number of samples that are used for making one step in the  stochastic gradient descent optimizer algorithm. Default is 1.
  * `pcd`: indicating whether Persistent Contrastive Divergence (PCD) is to  be used (true, default) or simple CD that initializes the Gibbs Chain with  the training sample (false)
  * `cdsteps`: number of Gibbs sampling steps for (persistent)  contrastive divergence, defaults to 1
  * `monitoring`: a function that is executed after each training epoch.  It takes an RBM and the epoch as arguments.  See also `monitored_fitrbm` for another way of monitoring.
  * `categories`: only relevant if `rbmtype = Softmax0BernoulliRBM`.  The number of categories as `Int`, if all variables have the same number  of categories, or as `Vector{Int}` that contains the number of categories  of the i'th categorical variable in the i'th entry.
  * `upfactor`, `downfactor`: If this function is used for pretraining a part of  a DBM, it is necessary to multiply the weights of the RBM with factors.
  * `sdlearningrate`/`sdlearningrates`: learning rate(s) for the  standard deviation if training a `GaussianBernoulliRBM` or  `GaussianBernoulliRBM2`. Ignored for other types of RBMs.  It usually must be much smaller than the learning rates for  the weights. By default it is 0.0, which means that the standard deviation  is not learned.
  * `startrbm`: start training with the parameters of the given RBM.  If this argument is specified, `nhidden` and `rbmtype` are ignored.
  * `optimizer`/`optimizers`: an object of type `AbstractOptimizer` or a vector of  them for each epoch. If specified, the optimization is performed as implemented  by the given optimizer type. By default, the `LoglikelihoodOptimizer`  with the `learningrate`/`learningrates` and `sdlearningrate`/`sdlearningrates`  is used. For other types of optimizers, the learning rates must be specified  in the `optimizer`. For more information on how to write your own optimizer,  see `AbstractOptimizer`.

See also: `monitored_fitrbm` for a convenient monitoring of the training.
