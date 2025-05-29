```
genus_representatives(L::QuadLat; max = inf, use_auto = true)
                                                    -> Vector{QuadLat}
```

Computes representatives for the isometry classes in the genus of $L$.

At most `max` representatives are returned. The use of automorphims can be disabled by setting `use_auto = false`.
