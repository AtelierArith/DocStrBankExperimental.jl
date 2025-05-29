Get superparts incident to part in acset.

If the subpart is indexed, this takes constant time; otherwise, it takes linear time. As with [`subpart`](@ref), both single and vectorized access, as well as chained access, are supported. Note that sequences of morphisms are supplied in the usual left-to-right order, so that

```
incident(g, x, [:src, :vattr])
```

returns the list of all edges whose source vertex has vertex attribute `x`.

If the chaining of subparts is given as a tuple (e.g.; (:src, :vattr)), then code generation is used to check that the subparts and their order is a valid composition and to improve performance.

Note that when the subpart is indexed, this function returns a view of the underlying index, which should not be mutated. To ensure that a fresh copy is returned, regardless of whether indexing is enabled, set the keyword argument `copy=true`.
