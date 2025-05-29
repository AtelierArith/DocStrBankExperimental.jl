```
group(iter)
group(by::Union{Function, Type}, iter)
group(by::Union{Function, Type}, f::Union{Function, Type}, iter...)
```

イテラブル `iter` の要素 `x` のグループを `by(x)` でラベル付けされたグループに辞書として返します。各要素は `f(x)` に変換され、`by` と `f` はデフォルトで `identity` 関数になります。複数のコレクション（同じ長さのもの）が提供される場合、変換 `by` と `f` は要素ごとに行われます。

# 例

```jldoctest
julia> group(iseven, [1, 2, 3, 4, 5, 6, 7, 8, 9, 10])
Dictionary{Bool,Array{Int64,1}} with 2 entries:
 false │ [1, 3, 5, 7, 9]
 true  │ [2, 4, 6, 8, 10]

julia> group(iseven, x -> x ÷ 2, [1, 2, 3, 4, 5, 6, 7, 8, 9, 10])
Dictionary{Bool,Array{Int64,1}} with 2 entries:
 false │ [0, 1, 2, 3, 4]
 true  │ [1, 2, 3, 4, 5]
```
