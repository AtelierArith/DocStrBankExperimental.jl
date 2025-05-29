```
X <: XDim

X(val=:)
```

X [`Dimension`](@ref). `X <: XDim <: IndependentDim`

## Example:

```julia
xdim = X(2:2:10)
# Or
val = A[X(1)]
# Or
mean(A; dims=X)
```
