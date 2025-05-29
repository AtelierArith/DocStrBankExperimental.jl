```julia
vmean(A; dims, multithreaded=false)
```

`A`のすべての要素の平均を計算します。オプションで、`dims`で指定された次元に対して計算できます。`Statistics.mean`と同様ですが、ベクトル化されており（オプションで）マルチスレッド対応です。

## 例

```julia
julia> using VectorizedStatistics

julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> vmean(A, dims=1)
1×2 Matrix{Float64}:
 2.0  3.0

julia> vmean(A, dims=2)
2×1 Matrix{Float64}:
 1.5
 3.5
```
