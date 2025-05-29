```
insert(trie::HAMT{K, V}, key::K, val::V) where {K, V})
```

永続的な挿入。

```julia
dict = HAMT{Int, Int}()
dict = insert(dict, 10, 12)
```
