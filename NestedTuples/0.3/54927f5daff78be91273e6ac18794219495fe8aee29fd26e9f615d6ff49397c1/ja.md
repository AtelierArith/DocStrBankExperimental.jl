```
keysort(nt::NamedTuple)
```

NamedTupleのキーを再帰的にソートします。

例:

```
julia> x = randnt(3,2)
(p = (z = :z, e = :e, s = :s), w = (g = :g, o = :o), g = (c = :c, f = :f, k = :k))

julia> keysort(x)
(g = (c = :c, f = :f, k = :k), p = (e = :e, s = :s, z = :z), w = (g = :g, o = :o))
```
