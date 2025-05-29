```
point!(builder,x)
point!(builder,x,y)
point!(builder,x,y,z)
point!(builder,vec_or_tuple)
```

Add point or merge with already existing point. Returns its index which can be used to set up facets with [`facet!`](@ref).
