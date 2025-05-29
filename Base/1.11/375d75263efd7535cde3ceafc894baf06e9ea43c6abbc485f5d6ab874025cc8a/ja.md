```
setindex(nt::NamedTuple, val, key::Symbol)
```

キー `key` を `val` に設定した新しい `NamedTuple` を構築します。もし `key` がすでに `nt` のキーに含まれている場合、`val` は古い値を置き換えます。

```jldoctest
julia> nt = (a = 3,)
(a = 3,)

julia> Base.setindex(nt, 33, :b)
(a = 3, b = 33)

julia> Base.setindex(nt, 4, :a)
(a = 4,)

julia> Base.setindex(nt, "a", :a)
(a = "a",)
```
