```julia
inplace_linsolve!(A, b)

```

Non-allocating, non-pivoting inplace solution of square linear system of equations `A*x=b` using [Doolittle's method](https://en.wikipedia.org/wiki/LU_decomposition#Doolittle_algorithm).

After solution, `A` will contain the LU factorization, and `b` the result.

A pivoting version is available with Julia v1.9.
