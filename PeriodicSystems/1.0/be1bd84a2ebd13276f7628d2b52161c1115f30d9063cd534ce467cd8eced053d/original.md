```
 pszero(psys::PeriodicStateSpace{PeriodicMatrix}[, K]; atol, rtol, fast) -> val
 pszero(psys::PeriodicStateSpace{PeriodicArray}[, K]; atol, rtol, fast) -> val
```

Compute the finite and infinite zeros of a discrete-time periodic system `psys = (A(t), B(t), C(t), D(t))` in `val`,  where the periodic system matrices `A(t)`, `B(t)`, `C(t)`, and `D(t)` are in either *Periodic Matrix* or *Periodic Array* representation.  The optional argument `K` specifies a desired time to start the sequence of periodic matrices (default: `K = 1`).

The computation of zeros relies on the *fast* structure exploiting reduction of singular periodic pencils as described in [1],  which separates a matrix pencil `M-λN` which contains the infinite and finite zeros  and the left and right Kronecker indices. The reduction is performed using orthonal similarity transformations and involves rank decisions based  on rank revealing QR-decompositions with column pivoting,  if `fast = true`, or, the more reliable, SVD-decompositions, if `fast = false`. 

The keyword arguments `atol` and `rtol` specify the absolute and relative tolerances for the nonzero elements of the periodic system matrices, respectively.  The default relative tolerance is `n*ϵ`, where `n` is proportional with the largest dimension of the periodic matrices,  and `ϵ` is the working machine epsilon. 

*References*

[1] A. Varga and P. Van Dooren. Computing the zeros of periodic descriptor systems.     Systems & Control Letters 50:371–381, 2003.
