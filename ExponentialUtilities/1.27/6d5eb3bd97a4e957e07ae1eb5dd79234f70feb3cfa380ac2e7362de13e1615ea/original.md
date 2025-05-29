```
expv(t,A,b; kwargs) -> exp(tA)b
```

Compute the matrix-exponential-vector product using Krylov.

A Krylov subspace is constructed using `arnoldi` and `exp!` is called on the Hessenberg matrix. Consult `arnoldi` for the values of the keyword arguments. An alternative algorithm, where an error estimate generated on-the-fly is used to terminate the Krylov iteration, can be employed by setting the kwarg `mode=:error_estimate`.

```
expv(t,Ks; cache) -> exp(tA)b
```

Compute the expv product using a pre-constructed Krylov subspace.
