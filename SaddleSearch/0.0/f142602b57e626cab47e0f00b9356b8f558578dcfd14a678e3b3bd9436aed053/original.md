`BBDimer`: dimer method with Barzilai-Borwein step-size + an Armijo type stability check.

### Parameters:

  * `a0_trans` : initial translation step
  * `a0_rot` : initial rotation step
  * `ls` : linesearch

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

## References

The method combines ideas from

[ZDZ] Optimization-based Shrinking Dimer Method for Finding Transition States SIAM J. Sci. Comput., 38(1), A528–A544 Lei Zhang, Qiang Du, and Zhenzhen Zheng DOI:10.1137/140972676

and

[GOP] A dimer-type saddle search algorithm with preconditioning and linesearch Math. Comp. 85, 2016 N. Gould and C. Ortner and D. Packwood http://arxiv.org/abs/1407.2817
