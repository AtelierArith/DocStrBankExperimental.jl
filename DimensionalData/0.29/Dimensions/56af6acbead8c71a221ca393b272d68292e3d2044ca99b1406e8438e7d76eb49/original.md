```
Z <: ZDim

Z(val=:)
```

Z [`Dimension`](@ref). `Z <: ZDim <: Dimension`

## Example:

```julia
zdim = Z(10:10:100)
```

```julia
val = A[Z(1)]
```

```julia
mean(A; dims=Z)
```
