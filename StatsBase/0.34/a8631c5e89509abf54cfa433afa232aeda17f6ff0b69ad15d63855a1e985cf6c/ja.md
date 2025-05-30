```
indicatormat(x, k::Integer; sparse=false)
```

サイズ `(k, length(x))` のブール行列 `I` を構築します。ここで `I[x[i], i] = true` となり、他のすべての要素は `false` に設定されます。`sparse` が `true` の場合、出力はスパース行列になります。そうでない場合は密行列（デフォルト）になります。

# 例

```jldoctest
julia> using StatsBase

julia> indicatormat([1 2 2], 2)
2×3 Matrix{Bool}:
 1  0  0
 0  1  1
```
