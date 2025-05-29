```
psa_abscissa(A,ϵ [,d]) -> α,z
```

Compute ϵ-pseudospectral abscissa for a dense matrix.

Quadratically convergent two-way method to compute the ϵ-pseudospectral abscissa `α` of a dense matrix `A`. Also returns a vector `z` of points where the pseudospectrum reaches the abscissa. Uses the criss-cross algorithm of Burke et al.

The ϵ-pseudospectral abscissa is

```
   maximum(real(z)) for z s.t. minimum(σ(A-zI)) == ϵ
```

Optional arg:

  * `d`: eigenvalues of A, if known in advance

Keyword args:

  * `verbosity: 0 for quiet, 1 for noise
