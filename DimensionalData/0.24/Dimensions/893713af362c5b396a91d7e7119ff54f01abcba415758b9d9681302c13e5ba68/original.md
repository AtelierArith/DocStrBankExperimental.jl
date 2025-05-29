```
Z <: ZDim

Z(val=:)
```

Z [`Dimension`](@ref). `Z <: ZDim <: Dimension`

## Example:

```julia
zdim = Z(10:10:100)
# Or
val = A[Z(1)]
# Or
mean(A; dims=Z)
```
