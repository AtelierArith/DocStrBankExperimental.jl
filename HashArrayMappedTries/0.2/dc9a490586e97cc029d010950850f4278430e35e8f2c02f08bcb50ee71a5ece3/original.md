```
insert(trie::HAMT{K, V}, key::K, val::V) where {K, V})
```

Persitent insertion.

```julia
dict = HAMT{Int, Int}()
dict = insert(dict, 10, 12)
```
