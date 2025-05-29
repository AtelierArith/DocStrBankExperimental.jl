Get subpart of part in acset.

Both single and vectorized access are supported, with a view of the underlying data being returned in the latter case. Chaining, or composition, of subparts is also supported. For example, given a vertex-attributed graph `g`,

```
subpart(g, e, [:src, :vattr])
```

returns the vertex attribute of the source vertex of the edge `e`. As a shorthand, subparts can also be accessed by indexing:

```
g[e, :src] == subpart(g, e, :src)
```

If the chaining of subparts is given as a tuple (e.g.; (:src, :vattr)), then code generation is used to check that the subparts and their order is a valid composition and to improve performance.

Be warned that indexing with lists of subparts works just like `subpart`: `g[e,[:src,:vattr]]` is equivalent to `subpart(g, e, [:src,:vattr])`. This convention differs from DataFrames but note that the alternative interpretation of `[:src,:vattr]` as two independent columns does not even make sense, since they have different domains (belong to different tables).
