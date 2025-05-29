```julia
nanmean(A; dims)
```

`A`のすべての非`NaN`要素の平均を計算します。オプションで、`dims`で指定された次元に対して計算します。`Statistics.mean`と同様ですが、`NaN`を無視します。

`dims`の代わりに、`nanmean`は`dim`キーワードもサポートしており、これは`dims`と同様に動作しますが、削減された任意の単一次元をドロップします（これは他の言語の慣例です）。

## 例

```julia
julia> using NaNStatistics

julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> nanmean(A, dims=1)
1×2 Matrix{Float64}:
 2.0  3.0

julia> nanmean(A, dims=2)
2×1 Matrix{Float64}:
 1.5
 3.5
```
