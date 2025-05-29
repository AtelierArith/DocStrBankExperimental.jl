```
algebra_structures(X::Object)
algebra_structures(X::Object, unit::Morphism)
```

Return a set of algebra objects over $X$. An empty array is returned only if there are no algebra structures. If the algebr is not connected, i.e. $Hom(𝟙,X) ≠ k$, then a unit should be provided.
