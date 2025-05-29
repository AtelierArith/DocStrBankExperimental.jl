```
rect2d!(builder, sw, ne; facetregions=nothing)
```

Add points and facets describing a rectangle via points describing its south-west and north-east corners. On default, the corresponding facet regions are deduced from the current facetregion. Alternatively,  a 4-vector of facetregions can be passed.
