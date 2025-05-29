```
is_primitive(L::ZZLat, v::Union{Vector, QQMatrix}) -> Bool
```

Return whether the vector `v` is primitive in `L`.

A vector `v` in a $\mathbb Z$-lattice `L` is called primitive if for all `w` in `L` such that $v = dw$ for some integer `d`, then $d = \pm 1$.
