```
stackrbms(x; ...)
```

Performs greedy layerwise training for Deep Belief Networks or greedy layerwise pretraining for Deep Boltzmann Machines and returns the trained model.

# Optional keyword arguments (ordered by importance):

  * `predbm`: boolean indicating that the greedy layerwise training is  pre-training for a DBM.  If its value is false (default), a DBN is trained.
  * `nhiddens`: vector containing the number of nodes of the i'th hidden layer in  the i'th entry
  * `epochs`: number of training epochs
  * `learningrate`: learningrate, default 0.005
  * `batchsize`: size of minibatches, defaults to 1
  * `trainlayers`: a vector of `TrainLayer` objects. With this argument it is possible  to specify the training parameters for each layer/RBM individually.  If the number of training epochs and the learning rate are not specified  explicitly for a layer, the values of `epochs` and `learningrate` are used.  For more information see help of `TrainLayer`.
  * `monitoringdata`: a data dictionary (see type `DataDict`)  The data is propagated forward through the  network to monitor higher levels.  If a non-empty dictionary is given, the monitoring functions in the  `trainlayers`-arguments must accept a `DataDict` as third argument.
  * `optimizer`: an optimizer (of type `AbstractOptimizer`) that is used for  computing the gradients when training the individual RBMs.
  * `samplehidden`: boolean indicating that consequent layers are to be trained  with sampled values instead of the deterministic potential.  Using the deterministic potential (`false`) is the default.

See also: `monitored_stackrbms` for a more convenient monitoring.
