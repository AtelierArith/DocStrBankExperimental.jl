```
Z <: ZDim

Z(val=:)
```

Z [`次元`](@ref). `Z <: ZDim <: 次元`

## 例:

```julia
zdim = Z(10:10:100)
# または
val = A[Z(1)]
# または
mean(A; dims=Z)
```
