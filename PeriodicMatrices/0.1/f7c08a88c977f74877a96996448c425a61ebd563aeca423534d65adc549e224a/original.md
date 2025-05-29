```
 phess(A::Array{Float64,3}; hind = 1, rev = true, withZ = true) -> (H, Z, ihess)
 phess1(A::Array{Float64,3}; hind = 1, rev = true, withZ = true) -> (H, Z, ihess)
```

Compute the Hessenberg decomposition of a product of square matrices  `A(p)*...*A(2)*A(1)`, if `rev = true` (default) or `A(1)*A(2)*...*A(p)` if `rev = false`, without evaluating the product.  The matrices `A(1)`, `...`, `A(p)` are contained in the `n×n×p` array `A`  such that the `i`-th matrix `A(i)` is contained in `A[:,:,i]`. The resulting `n×n×p` arrays `H` and `Z` contain the matrices `H(1)`, `...`, `H(p)` and the orthogonal matrices `Z(1)`, `...`, `Z(p)`, respectively,  such that for `rev = true`

```
       Z(2)' * A(1) * Z(1) = H(1),
       Z(3)' * A(2) * Z(2) = H(2),
              ...
       Z(1)' * A(p) * Z(p) = H(p),
```

and for `rev = false`

```
       Z(1)' * A(1) * Z(2) = H(1),
       Z(2)' * A(2) * Z(3) = H(2),
              ...
       Z(p)' * A(p) * Z(1) = H(p).
```

If `hind = ihess`, with `1 ≤ ihess ≤ p` (default `ihess = 1`), then  `H(i)`, `i = 1, ..., p` are in a periodic Hessenberg form,  with `H(ihess)` in upper Hessenberg form and `H(i)`  upper triangular for `i` $\neq$ `ihess`.  `H(i)` and `Z(i)` are contained in `H[:,:,i]` and `Z[:,:,i]`, respectively.  The performed orthogonal transformations are not accumulated if `withZ = false`,  in which case `Z = nothing`. 

The function `phess` is based on a wrapper for the SLICOT subroutine `MB03VW`    (see [`PeriodicMatrices.SLICOTtools.mb03vw!`](@ref)).

The function `phess1` is based on wrappers for the SLICOT subroutines `MB03VD`   (see [`PeriodicMatrices.SLICOTtools.mb03vd!`](@ref)) and `MB03VY`  (see [`PeriodicMatrices.SLICOTtools.mb03vy!`](@ref)).
