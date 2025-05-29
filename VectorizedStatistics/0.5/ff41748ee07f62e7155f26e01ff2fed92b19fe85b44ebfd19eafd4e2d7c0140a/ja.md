```julia
vminimum(A; dims)
```

`A`に含まれる最小値を見つけます。オプションで、`dims`で指定された次元に対しても可能です。`Base.minimum`と同様ですが、ベクトル化されています。

## 例

```julia
julia> using VectorizedStatistics

julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> vminimum(A, dims=1)
1×2 Matrix{Int64}:
 1  2

julia> vminimum(A, dims=2)
 2×1 Matrix{Int64}:
 1
 3
```
