```julia
nanstd(A; dims=:, mean=nothing, corrected=true)
```

`A`のすべての非`NaN`要素の分散を計算します。オプションで、`dims`で指定された次元に対して計算できます。`Statistics.var`と同様ですが、`NaN`を無視します。

事前に計算された`mean`をオプションで提供することができ、これにより計算が若干速くなります。`corrected`が`true`の場合、*ベッセルの補正*が適用され、合計は`n`ではなく`n-1`で割られます。

`dims`の代わりに、`nanstd`は`dim`キーワードもサポートしており、これは`dims`と同様に動作しますが、削減された単一次元をドロップします（これは他のいくつかの言語での慣例です）。

## 例

```julia
julia> using NaNStatistics

julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> nanstd(A, dims=1)
1×2 Matrix{Float64}:
 1.41421  1.41421

julia> nanstd(A, dims=2)
2×1 Matrix{Float64}:
 0.7071067811865476
 0.7071067811865476
```
