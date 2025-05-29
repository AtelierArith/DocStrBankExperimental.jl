```
Y <: YDim

Y(val=:)
```

Y [`Dimension`](@ref). `Y <: YDim <: DependentDim`

## Examples

```julia
ydim = Y(['a', 'b', 'c'])
```

```julia
val = A[Y(1)]
```

```julia
mean(A; dims=Y)
```
