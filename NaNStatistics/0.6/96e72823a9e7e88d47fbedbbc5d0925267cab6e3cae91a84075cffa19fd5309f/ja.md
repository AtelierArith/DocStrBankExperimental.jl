```julia
nansem(A; dims=:, mean=nothing, corrected=true)
```

`A`のすべての非`NaN`要素の平均の標準誤差を計算します。オプションで、`dims`で指定された次元に対して計算できます。

事前に計算された`mean`をオプションで提供することができ、これにより計算が若干速くなります。`corrected`が`true`の場合、*ベッセルの補正*が適用され、合計は`n`ではなく`n-1`で割られます。

`dims`の代わりに、`nansem`は`dim`キーワードもサポートしており、これは`dims`と同様に動作しますが、削減された任意のシングルトン次元をドロップします（これは他のいくつかの言語での慣例です）。

## 例

```julia
julia> using NaNStatistics

julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> nansem(A, dims=1)
1×2 Matrix{Float64}:
 2.0  2.0

julia> nansem(A, dims=2)
2×1 Matrix{Float64}:
 0.5
 0.5
```
