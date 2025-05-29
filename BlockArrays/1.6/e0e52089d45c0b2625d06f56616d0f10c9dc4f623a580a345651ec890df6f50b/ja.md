```
blockpush!(dest::BlockVector, blocks...) -> dest
```

`blocks`を`dest`の末尾に追加します。

この関数は、`blocks`が`dest`と互換性がある場合、`blocks`の要素をコピーすることを避けます。重要なことに、これはその後に`blocks`を変更すると`dest`内のアイテムが変わることを意味し、`blocks`の長さが変更されると`dest`の不変性が破られる可能性があります。

# 例

```jldoctest
julia> using BlockArrays

julia> blockpush!(mortar([[1], [2, 3]]), [4, 5], [6])
4-blocked 6-element BlockVector{Int64}:
 1
 ─
 2
 3
 ─
 4
 5
 ─
 6
```
