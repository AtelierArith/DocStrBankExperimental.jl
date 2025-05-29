```
getpaduapoints([f::Function,], [T=Float64,] n)
```

は、次数 `n` のパドゥア点（型 `T`）で関数 `f` を評価します。

関数 `f` が提供されていない場合、`getpaduapoints` はパドゥア点の行列を返します。この行列の最初の列と第二の列はそれぞれ x 成分と y 成分を表します。もし `f` が単一の値を返す場合、`getpaduapoints` は `Vector{T}` を返します。もし `f` がタプルや他のインデックス可能なイテラブルを返す場合、`getpaduapoints` は `Matrix{T}` を返し、i 番目の列はすべてのパドゥア点に適用された `f` の i 番目の成分関数を表します。

# 例

```jldoctest
julia> getpaduapoints(2)
6×2 Matrix{Float64}:
  1.0   1.0
  1.0  -0.5
  0.0   0.5
  0.0  -1.0
 -1.0   1.0
 -1.0  -0.5

julia> getpaduapoints(Float32, 1)
3×2 Matrix{Float32}:
  1.0   1.0
  1.0  -1.0
 -1.0   0.0

julia> getpaduapoints(Float32, 2) do x, y; x*y; end
6-element Vector{Float32}:
  1.0
 -0.50000006
  0.0
 -0.0
 -1.0
  0.50000006

julia> getpaduapoints(2) do x, y; x*y, 5*x*y; end
6×2 Matrix{Float64}:
  1.0   5.0
 -0.5  -2.5
  0.0   0.0
 -0.0  -0.0
 -1.0  -5.0
  0.5   2.5
```
