```julia
vsum(A; dims, multithreaded=false)
```

`A`に含まれる値を合計します。オプションで、`dims`で指定された次元に対して合計できます。`Base.sum`と同様ですが、ベクトル化されており（オプションで）マルチスレッド対応です。

## 例

```julia
julia> using VectorizedStatistics

julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> vsum(A, dims=1)
1×2 Matrix{Int64}:
 4  6

julia> vsum(A, dims=2)
2×1 Matrix{Int64}:
 3
 7
```
