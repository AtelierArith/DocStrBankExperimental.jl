```julia
find_degenerate(w; digits)

```

リスト `w` の縮退値のインデックスを計算します。`w` は昇順にソートされている必要があります。

`digits` キーワード引数が提供されている場合、エネルギーを小数点以下の指定された桁数（または負の場合は小数点前）に基づいて四捨五入します。デフォルト値は 8 です。

# 例

```julia-repl
julia> w = [1,1,1,2,3,4,4,5]
julia> find_degenerate(w)
2-element Array{Array{Int64,1},1}:
 [1, 2, 3]
 [6, 7]
```
