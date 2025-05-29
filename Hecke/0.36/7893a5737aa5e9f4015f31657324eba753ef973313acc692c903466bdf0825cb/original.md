```
maximal_abelian_subfield(K::RelSimpleNumField{AbsSimpleNumFieldElem}; of_closure::Bool = false) -> ClassField
```

Using a probabilistic algorithm for the norm group computation, determine the maximal abelian subfield in $K$ over its base field. If `of_closure` is set to true, then the algorithm is applied to the normal closure of $K$ (without computing it).
