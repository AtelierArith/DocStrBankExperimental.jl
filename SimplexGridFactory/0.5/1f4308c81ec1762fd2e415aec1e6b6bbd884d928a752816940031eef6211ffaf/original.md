```
rect3d!(builder, bsw, tne; facetregions=nothing)
```

Add points and facets describing a qudrilateral via points describing its bottom south-west and top north-east corners. On default, the corresponding facet regions are deduced from the current facetregion. Alternatively,  a 6-vector of facetregions can be passed (in the sequence s-e-n-w-b-t)
