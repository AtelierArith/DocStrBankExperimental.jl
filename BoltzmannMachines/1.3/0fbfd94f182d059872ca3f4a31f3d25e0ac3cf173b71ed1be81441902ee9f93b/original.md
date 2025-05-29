Specify parameters for training one RBM-layer in a DBM.

# Optional keyword arguments:

  * The optional keyword arguments `rbmtype`, `nhidden`, `epochs`, `learningrate`/`learningrates`, `sdlearningrate`/`sdlearningrates`, `categories`, `batchsize`, `pcd`, `cdsteps`, `startrbm` and `optimizer`/`optimizers` are passed to `fitrbm`. For a detailed description, see there. If a negative value is specified for `learningrate` or `epochs`, this indicates that a corresponding default value should be used (parameter defined by call to `stackrbms`).
  * `monitoring`: also like in `fitrbm`, but may take a `DataDict` as third argument  (see function `stackrbms` and its argument `monitoringdata`).
  * `nvisible`: Number of visible units in the RBM. Only relevant for partitioning.  This parameter is derived as much as possible by `stackrbms`.  For `MultimodalDBM`s with a partitioned first layer, it is necessary to specify  the number of visible nodes for all but at most one partition in the input layer.
