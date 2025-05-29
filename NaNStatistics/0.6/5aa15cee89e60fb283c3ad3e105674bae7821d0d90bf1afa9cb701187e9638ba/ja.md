```julia
nanskewness(A; dims=:, mean=nothing)
```

`A`のすべての非`NaN`要素の歪度を計算します。オプションで、`dims`で指定された次元に対して計算できます。`NaN`を無視する点で、`StatsBase.skewness`と同様です。

事前に計算された`mean`をオプションで提供することができ、これにより計算が若干速くなります。

`dims`の代わりに、`nanskewness`は`dim`キーワードもサポートしており、これは`dims`と同様に動作しますが、削減された単一次元をドロップします（これは他の言語の慣例です）。

## 例

```julia
julia> using NaNStatistics

julia> A = [1 2 3 ; 4 5 6; 7 8 9]
3×3 Matrix{Int64}:
 1  2  3
 4  5  6
 7  8  9

julia> nanskewness(A, dims=1)
1×3 Matrix{Float64}:
 0.0  0.0  0.0


julia> nanskewness(A, dims=2)
3-element Vector{Float64}:
 0.0
 0.0
 0.0
```
