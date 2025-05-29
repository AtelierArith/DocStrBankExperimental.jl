```julia
vstd(A; dims=:, mean=nothing, corrected=true, multithreaded=false)
```

`A`のすべての要素の分散を計算します。オプションで、`dims`で指定された次元に対して計算することもできます。`Statistics.var`と同様ですが、ベクトル化されており（オプションで）マルチスレッド対応です。

事前に計算された`mean`をオプションで提供することができ、これにより計算が若干速くなります。`corrected`が`true`の場合、*ベッセルの補正*が適用され、合計は`n`ではなく`n-1`で割られます。

## 例

```julia
julia> using VectorizedStatistics

julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> vstd(A, dims=1)
1×2 Matrix{Float64}:
 1.41421  1.41421

julia> vstd(A, dims=2)
2×1 Matrix{Float64}:
 0.7071067811865476
 0.7071067811865476
```
