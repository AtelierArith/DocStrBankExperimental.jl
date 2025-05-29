```
VecJac(f, u, [p, t]; fu = nothing, autodiff = AutoFiniteDiff())
```

Returns SciMLOperators.FunctionOperator which computes vector-jacobian product `(df/du)ᵀ * v`.

!!! note
    For non-square jacobians with inplace `f`, `fu` must be specified, else `VecJac` assumes a square jacobian.


```julia
L = VecJac(f, u)

L * v         # = (df/du)ᵀ * v
mul!(w, L, v) # = (df/du)ᵀ * v

L(v, p, t; VJP_input = w)    # = (df/du)ᵀ * v
L(x, v, p, t; VJP_input = w) # = (df/du)ᵀ * v
```

## Allowed Function Signatures for `f`

For Out of Place Functions:

```julia
f(u, p, t)  # t !== nothing
f(u, p)     # p !== nothing
f(u)        # Otherwise
```

For In Place Functions:

```julia
f(du, u, p, t)  # t !== nothing
f(du, u, p)     # p !== nothing
f(du, u)        # Otherwise
```
