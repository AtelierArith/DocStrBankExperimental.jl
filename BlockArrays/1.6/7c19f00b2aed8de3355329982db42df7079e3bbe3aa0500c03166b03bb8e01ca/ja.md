```
blockpushfirst!(dest::BlockVector, blocks...) -> dest
```

`blocks`を`dest`の先頭に追加します。詳細は[`blockpush!`](@ref)を参照してください。

この関数は、`blocks`が`dest`と互換性がある場合、`blocks`の要素をコピーすることを避けます。重要なことに、これはその後に`blocks`を変更すると`dest`内のアイテムが変更され、`blocks`の長さが変更されると`dest`の不変性が破られる可能性があることを意味します。

# 例

```jldoctest
julia> using BlockArrays

julia> blockpushfirst!(mortar([[1], [2, 3]]), [4, 5], [6])
4-blocked 6-element BlockVector{Int64}:
 4
 5
 ─
 6
 ─
 1
 ─
 2
 3
```
