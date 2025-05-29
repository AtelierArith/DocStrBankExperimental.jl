```
X <: XDim

X(val=:)
```

X [`Dimension`](@ref). `X <: XDim <: IndependentDim`

## Examples

```julia
xdim = X(2:2:10)
```

```julia
val = A[X(1)]
```

```julia
mean(A; dims=X)
```
