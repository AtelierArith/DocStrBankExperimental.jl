```
Poisson{N,M}
```

Composite type for conservative variable coefficient Poisson equations:

```
∮ds β ∂x/∂n = σ
```

The resulting linear system is

```
Ax = [L+D+L']x = z
```

where A is symmetric, block-tridiagonal and extremely sparse. Moreover,  `D[I]=-∑ᵢ(L[I,i]+L'[I,i])`. This means matrix storage, multiplication, ect can be easily implemented and optimized without external libraries.

To help iteratively solve the system above, the Poisson structure holds helper arrays for `inv(D)`, the error `ϵ`, and residual `r=z-Ax`. An iterative solution method then estimates the error `ϵ=̃A⁻¹r` and increments `x+=ϵ`, `r-=Aϵ`.
