```
GetHess!(ADmode::Val, F::Function; kwargs...) -> Function
```

Returns a function which computes Hessians in-place via a backend specified by `ADmode`. The function returned by `GetHess!` has argument structure `(Y::AbstractMatrix, X::AbstractVector)` where the Hessian of `F` evaluated at `X` is saved into `Y`.

Example:

```julia
Hessian! = GetHess!(Val(:ForwardDiff), x->x[1]^2 -x[2]^3 + x[1]*x[2])
Y = Matrix{Float64}(undef, 2, 2)
Hessian!(Y, rand(2))
```

For available backends, see `diff_backends()`.
