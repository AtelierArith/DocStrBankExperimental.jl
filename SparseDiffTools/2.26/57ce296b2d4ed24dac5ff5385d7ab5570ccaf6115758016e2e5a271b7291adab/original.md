```
JacVec(f, u, [p, t]; fu = nothing, autodiff = AutoForwardDiff(), tag = DeivVecTag(),
    kwargs...)
```

Returns SciMLOperators.FunctionOperator which computes jacobian-vector product `df/du * v`.

!!! note
    For non-square jacobians with inplace `f`, `fu` must be specified, else `JacVec` assumes a square jacobian.


```julia
L = JacVec(f, u)

L * v         # = df/du * v
mul!(w, L, v) # = df/du * v

L(v, p, t)    # = df/dw * v
L(x, v, p, t) # = df/dw * v
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
