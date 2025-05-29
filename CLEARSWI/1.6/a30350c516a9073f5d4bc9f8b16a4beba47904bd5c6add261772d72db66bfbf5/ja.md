```
createIntensityProjection(S::AbstractArray{T,3}, func, d=7) where T
```

`S`の3次元にわたる強度投影を、`func`関数を用いて`d`スライスで計算します。良い関数には`minimum`、`maximum`、`mean`、`std`などがあります。

# 例

```julia-repl
julia> using Statistics
julia> a = rand(Float64, (64,64,20))
julia> createIntensityProjection(a, std)
```
