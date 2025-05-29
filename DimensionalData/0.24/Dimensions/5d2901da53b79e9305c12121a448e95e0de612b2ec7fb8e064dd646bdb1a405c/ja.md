```
X <: XDim

X(val=:)
```

X [`Dimension`](@ref). `X <: XDim <: IndependentDim`

## 例:

```julia
xdim = X(2:2:10)
# または
val = A[X(1)]
# または
mean(A; dims=X)
```
