```
module FMM2D
```

Wrappers for the Flatiron Institute's FMM2D library.

# List of wrappers

All N-body codes return output in an `FMMVals` structure. See documentation of N-body codes for details.

N-body interactions with the Helmholtz kernel

  * [`hfmm3d`](@ref): $O(N)$ fast mutlipole code for the Helmholtz kernel
  * [`h3ddir`](@ref): $O(N^2)$ direct code
  * [`lfmm3d`](@ref): $O(N)$ fast mutlipole code for the Laplace kernel
