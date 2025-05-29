```
Y <: YDim

Y(val=:)
```

Y [`Dimension`](@ref). `Y <: YDim <: DependentDim`

## 例

```julia
ydim = Y(['a', 'b', 'c'])
```

```julia
val = A[Y(1)]
```

```julia
mean(A; dims=Y)
```
