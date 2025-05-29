The `AbstractOptimizer` interface allows to specify optimization procedures. It consists of three methods:

  * `initialized(optimizer, bm)`: May be used for creating an optimizer that is  specifically initialized for the Boltzmann machine `bm`.  In particular it may be used to allocate reusable space for the gradient.  The default implementation simply returns the unmodified `optimizer`.
  * `computegradient!(optimizer, v, vmodel, h, hmodel, rbm)` or `computegradient!(optimizer, meanfieldparticles, gibbsparticles, dbm)`  needs to be implemented for computing the gradient given the samples  from the positive and negative phase.
  * `updateparameters!(bm, optimizer)` needs to be specified for taking the  gradient step. The default implementation for RBMs expects the fields  `learningrate` and `gradient` and adds `learningrate * gradient` to the  given RBM.
