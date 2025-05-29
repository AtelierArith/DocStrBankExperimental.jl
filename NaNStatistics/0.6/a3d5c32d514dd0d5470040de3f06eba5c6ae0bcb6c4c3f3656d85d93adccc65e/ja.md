```julia
nansum(A; dims)
```

インデックス可能なコレクション `A` の合計を計算し、`NaN` を無視します。オプションで、`dims` で指定された次元に沿って計算します。

また、`dim` キーワードもサポートしており、これは `dims` と同様に動作しますが、削減された単一の次元をドロップします（これは他の言語の慣習です）。

## 例

```julia
julia> using NaNStatistics

julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> nansum(A, dims=1)
1×2 Matrix{Int64}:
 4  6

julia> nansum(A, dims=2)
2×1 Matrix{Int64}:
 3
 7
```
