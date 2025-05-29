`SuperlinearDimer`: dimer variant based on Kastner's JCP 128, 014106 (2008) article & ASE implementation

### Parameters

  * maximum_translation : control step-size (actual, not the parameter)
  * max*num*rot : maximum number of rotations at each step
  * trial_angle : angle increment to predict change in energy after rotation
  * trial*trans*step : step increment to predict change in energy after translation
  * use*central*forces : ???
  * extrapolate : whether or not to do the Kastner extrapolation
  * translation_method : only "CG" is implemented

### Shared Parameters

  * `tol_trans` : translation residual tolerance
  * `tol_rot` : rotation residual tolerance
  * `maxnumdE` : maximum number of dE evalluations
  * `len` : dimer-length (i.e. distance of the two walkers)
  * `precon` : preconditioner
  * `precon_prep!` : update function for preconditioner
  * `verbose` : how much information to print (0: none, 1:end of iteration, 2:each iteration, 3:file log)
  * `precon_rot` : true/false whether to precondition the rotation step
  * `rescale_v` : should `v` be rescaled to unit length after each step
