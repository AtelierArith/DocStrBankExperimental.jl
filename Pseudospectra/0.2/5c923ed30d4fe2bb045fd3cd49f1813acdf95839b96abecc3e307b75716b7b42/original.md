```
psa_radius(A,ϵ [,d]) -> r,z
```

Compute ϵ-pseudospectral radius for a dense matrix.

Quadratically convergent two-way method to compute the ϵ-pseudospectral radius `r` of a dense matrix `A`. Also returns a vector `z` of points where the pseudospectrum intersects the circle of radius `r`. Uses the "criss-cross" algorithm of Overton and Mengi.

The ϵ-pseudospectral radius is

```
   maximum(abs(z)) for z s.t. minimum(σ(A-zI)) == ϵ
```

Optional arg:

  * `d`: eigenvalues of A, if known in advance

Keyword args:

  * `verbosity: 0 for quiet, 1 for noise
