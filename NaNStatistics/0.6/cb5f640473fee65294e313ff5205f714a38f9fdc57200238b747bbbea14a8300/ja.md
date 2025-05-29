```julia
nankurtosis(A; dims=:, mean=nothing)
```

`A`のすべての非`NaN`要素の尖度を計算します。オプションで、`dims`で指定された次元に対して計算できます。`StatsBase.kurtosis`と同様ですが、`NaN`を無視します。

事前に計算された`mean`をオプションで提供することができ、これにより計算が若干速くなります。`corrected`が`true`の場合、*ベッセルの補正*が適用され、合計は`n`ではなく`n-1`で割られます。

`dims`の代わりに、`nankurtosis`は`dim`キーワードもサポートしており、これは`dims`と同様に動作しますが、削減された任意の単一次元をドロップします（これは他のいくつかの言語の慣例です）。

## 例

```julia
julia> using NaNStatistics

julia> A = [1 2 3 ; 4 5 6; 7 8 9]
3×3 Matrix{Int64}:
 1  2  3
 4  5  6
 7  8  9

julia> nankurtosis(A, dims=1)
1×3 Matrix{Float64}:
 -1.5  -1.5  -1.5

julia> nankurtosis(A, dims=2)
3-element Vector{Float64}:
 -1.5
 -1.5
 -1.5
```
