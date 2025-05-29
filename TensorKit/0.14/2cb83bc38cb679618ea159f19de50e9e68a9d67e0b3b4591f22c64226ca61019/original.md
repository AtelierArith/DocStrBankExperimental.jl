```
infimum(V₁::ElementarySpace, V₂::ElementarySpace, V₃::ElementarySpace...)
```

Return the infimum of a number of elementary spaces, i.e. an instance `V::ElementarySpace` such that `V ≾ V₁`, `V ≾ V₂`, ... and no other `W ≻ V` has this property. This requires that all arguments have the same value of `isdual( )`, and also the return value `V` will have the same value.
