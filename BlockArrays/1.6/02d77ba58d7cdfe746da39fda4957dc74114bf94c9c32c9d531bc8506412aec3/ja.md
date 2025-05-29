```
blockappend!(dest::BlockVector, sources...) -> dest
```

`sources` から `dest` にブロックを追加します。 `dest` のブロックの数は `sum(blocklength, sources)` によって増加します。

この関数は、`sources` のブロックが `dest` と互換性がある場合、`sources` のブロックの要素をコピーすることを避けます。重要なことに、これは `sources` をその後変更すると `dest` のアイテムが変わり、`sources` の長さが変更されると `dest` の不変性が破られる可能性があることを意味します。

`dest` のブロックは `sources` またはその構成要素とエイリアスしてはいけません。たとえば、`blockappend!(x, x)` の結果は未定義です。

# 例

```jldoctest
julia> using BlockArrays

julia> blockappend!(mortar([[1], [2, 3]]), mortar([[4, 5]]))
3-blocked 5-element BlockVector{Int64}:
 1
 ─
 2
 3
 ─
 4
 5
```
