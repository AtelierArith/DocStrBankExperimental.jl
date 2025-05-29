`StaticDimer`: the most basic dimer variant, simply taking alternating steps with a fixed step-size.

### Parameters:

  * `a_trans` : translation step
  * `a_rot` : rotation step

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
