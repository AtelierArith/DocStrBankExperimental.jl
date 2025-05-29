```
fitdbm(x; ...)
```

Fits a (multimodal) DBM to the data set `x`. The procedure consists of two parts: First a stack of RBMs is pretrained in a greedy layerwise manner (see `stackrbms(x)`). Then the weights of all layers are jointly trained using the general Boltzmann Machine learning procedure (fine tuning, see `traindbm!(dbm,x)`).

# Optional keyword arguments (ordered by importance):

  * `nhiddens`: vector that defines the number of nodes in the hidden layers of  the DBM. The default value specifies two hidden layers with the same size  as the visible layer.
  * `epochs`: number of training epochs for joint training, defaults to 10
  * `epochspretraining`: number of training epochs for pretraining,  defaults to `epochs`
  * `learningrate`: learning rate for pretraining.  Also used as initial value for the decaying fine tuning learning rate.
  * `learningratepretraining`: learning rate for pretraining,  defaults to `learningrate`
  * `learningratefinetuning`: initial learning rate for fine tuning.  The learning rate for fine tuning is decaying with the number of epochs,  starting with the given value for the `learningratefinetuning` or the `learningrate`.  (For more details see `traindbm!`.)
  * `learningratesfinetuning`:  The learning rate for fine tuning is by default decaying with the number of epochs,  starting with the value of the `learningrate`.  (For more details see `traindbm!`.)  The value of the learning rate for each epoch of fine tuning can be specified  via the argument `learningratesfinetuning` as a vector  with an entry for each of the epochs.
  * `learningrates`: deprecated, otherwise equivalent to `learningratesfinetuning`
  * `batchsize`: number of samples in mini-batches for pretraining and fine tuning.  By default, a batchsize of 1 is used for pretraining.  For fine tuning, no mini-batches are used by default, which means that  the complete data set is used for calculating the gradient in each epoch.
  * `batchsizepretraining`: batchsize for pretraining, defaults to 1
  * `batchsizefinetuning`: batchsize for fine tuning. Defaults to the number of samples  in the data set, i.e., no mini batches are used.
  * `nparticles`: number of particles used for sampling during joint training of  DBM, default 100
  * `pretraining`: The arguments for layerwise pretraining  can be specified for each layer individually.  This is done via a vector of `TrainLayer` objects.  (For a detailed description of the possible parameters,  see help for `TrainLayer`).  If the number of training epochs and the learning rate are not specified  explicitly for a layer, the values of `epochspretraining`,  `learningratepretraining` and `batchsizepretraining` are used.
  * `monitoring`: Monitoring function accepting a `dbm` and the number of epochs,  returning nothing. Used for the monitoring of fine-tuning.  See also `monitored_fitdbm` for a more convenient way of monitoring.
  * `monitoringdatapretraining`: a `DataDict` that contains data used for  monitoring the pretraining (see argument `monitoringdata` of `stackrbms`.)
  * `optimizer`/`optimizers`: an optimizer or a vector of optimizers for each epoch  (see `AbstractOptimizer`) used for fine-tuning.
  * `optimizerpretraining`: an optimizer used for pre-training.  Defaults to the `optimizer`.
