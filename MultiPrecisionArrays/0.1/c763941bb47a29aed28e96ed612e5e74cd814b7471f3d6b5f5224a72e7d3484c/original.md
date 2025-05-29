mpglu!(MPGA::MPGArray; residterm=residtermdefault) Factor a MPGArray using the allocations from the structure.

This function factors the low precision copy and leaves the high precision matrix alone. The constructor  for MPGArray allocates storage for `basissize` Kylov vectors and some other things GMRES needs. You get a factorization object as output and can use `\` to solve linear systems.

The kwarg `residterm` sets the termination criterion.  `residterm == true` (default) terminates the iteration on  small residuals.  `residterm == false` terminates the iteration on small normwise backward errors. Look at the docs for details.
