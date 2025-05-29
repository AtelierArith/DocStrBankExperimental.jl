```
Band <: Dimension

Band(val=:)
```

マルチバンドラスター用のBand [`Dimension`](https://rafaqz.github.io/DimensionalData.jl/stable/api/reference#DimensionalData.Dimensions.Dimension)。

## 例:

```julia
banddim = Band(10:10:100)
# または
val = A[Band(1)]
# または
mean(A; dims=Band)
```
