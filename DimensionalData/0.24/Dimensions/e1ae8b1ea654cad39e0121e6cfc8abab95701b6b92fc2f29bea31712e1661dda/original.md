```
Y <: YDim

Y(val=:)
```

Y [`Dimension`](@ref). `Y <: YDim <: DependentDim`

## Example:

```julia
ydim = Y(['a', 'b', 'c'])
# Or
val = A[Y(1)]
# Or
mean(A; dims=Y)
```
