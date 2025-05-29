```
Y <: YDim

Y(val=:)
```

Y [`Dimension`](@ref). `Y <: YDim <: DependentDim`

## 例:

```julia
ydim = Y(['a', 'b', 'c'])
# または
val = A[Y(1)]
# または
mean(A; dims=Y)
```
