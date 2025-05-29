```
pairwise(dist::StringDistance, xs::AbstractVector, ys::AbstractVector = xs; preprocess = true)
```

`xs` と `ys` のすべての要素のペア間の距離を `StringDistance` `dist` に従って計算します。戻り値は行列 R であり、`R[i, j]` は `xs[i]` と `ys[j]` の間の距離に対応します。

前処理を使用しない場合は、`preprocess` を false に設定してください。

対称バージョンと非対称バージョンの両方が利用可能です。

### 例

```julia-repl
julia> using StringDistances
julia> iter = ["New York", "Princeton"]
julia> pairwise(Levenshtein(), iter)
2×2 Array{Float64,2}:
 0.0  9.0
 9.0  0.0
julia> iter2 = ["San Francisco"]
julia> pairwise(Levenshtein(), iter, iter2)
2×1 Array{Float64,2}:
 12.0
 10.0
```
