```
SimpleGMRES(; restart::Bool = true, blocksize::Int = 0, warm_start::Bool = false,
    memory::Int = 20)
```

A simple GMRES implementation for square non-Hermitian linear systems.

This implementation handles Block Diagonal Matrices with Uniformly Sized Square Blocks with specialized dispatches.

## Arguments

  * `restart::Bool`: If `true`, then the solver will restart after `memory` iterations.
  * `memory::Int = 20`: The number of iterations before restarting. If restart is false, this value is used to allocate memory and later expanded if more memory is required.
  * `blocksize::Int = 0`: If blocksize is `> 0`, the solver assumes that the matrix has a uniformly sized block diagonal structure with square blocks of size `blocksize`. Misusing this option will lead to incorrect results.

      * If this is set `≤ 0` and during runtime we get a Block Diagonal Matrix, then we will check if the specialized dispatch can be used.

!!! warning
    Most users should be using the `KrylovJL_GMRES` solver instead of this implementation.


!!! tip
    We can automatically detect if the matrix is a Block Diagonal Matrix with Uniformly Sized Square Blocks. If this is the case, then we can use a specialized dispatch. However, on most modern systems performing a single matrix-vector multiplication is faster than performing multiple smaller matrix-vector multiplications (as in the case of Block Diagonal Matrix). We recommend making the matrix dense (if size permits) and specifying the `blocksize` argument.

