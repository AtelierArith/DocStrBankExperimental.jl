```julia
nancumsum(A; dims)
```

インデックス可能なコレクション `A` の合計を計算し、`NaN` を無視します。オプションで、`dims` で指定された次元に沿って計算できます。

## 例

```julia
julia> using NaNStatistics

julia> A = [1 2; 3 4; NaN NaN]
3×2 Matrix{Float64}:
   1.0    2.0
   3.0    4.0
 NaN    NaN

julia> nancumsum(A, dims=1)
3×2 Matrix{Float64}:
 1.0  2.0
 4.0  6.0
 4.0  6.0

julia> nancumsum(vec(A))
6-element Vector{Float64}:
  1.0
  4.0
  4.0
  6.0
 10.0
 10.0
```
