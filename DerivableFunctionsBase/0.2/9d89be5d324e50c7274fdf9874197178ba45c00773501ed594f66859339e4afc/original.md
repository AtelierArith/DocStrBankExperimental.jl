```
GetGrad!(ADmode::Val, F::Function; kwargs...) -> Function
```

Returns a function which computes gradients in-place via a backend specified by `ADmode`. The function returned by `GetGrad!` has argument structure `(Y::AbstractVector, X::AbstractVector)` where the gradient of `F` evaluated at `X` is saved into `Y`.

Example:

```julia
Gradient! = GetGrad!(Val(:ForwardDiff), x->x[1]^2 - x[2]^3)
Y = Vector{Float64}(undef, 2)
Gradient!(Y, rand(2))
```

For available backends, see `diff_backends()`.
