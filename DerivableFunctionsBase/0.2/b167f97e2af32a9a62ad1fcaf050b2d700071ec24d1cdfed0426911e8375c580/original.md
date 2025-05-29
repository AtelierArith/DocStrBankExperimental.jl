```
GetMatrixJac!(ADmode::Val, F::Function; kwargs...) -> Function
```

Returns a function which computes Jacobians in-place for array-valued functions via a backend specified by `ADmode`. The function returned by `GetMatrixJac!` has argument structure `(Y::AbstractArray, X::AbstractVector)` where the Jacobian of `F` evaluated at `X` is saved into `Y`.

Example:

```julia
Jacobian! = GetMatrixJac!(Val(:ForwardDiff), x->[x[1]^2 x[2]^3; x[1]*x[2] 2])
Y = Array{Float64}(undef, 2, 2, 2)
Jacobian!(Y, rand(2))
```

For available backends, see `diff_backends()`.
