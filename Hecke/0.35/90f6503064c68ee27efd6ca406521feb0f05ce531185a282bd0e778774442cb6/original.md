```
automorphism_group_generators(L::AbstractLat; ambient_representation::Bool = true,
                                              depth::Int = -1, bacher_depth::Int = 0)
                                                      -> Vector{MatElem}
```

Given a definite lattice `L`, return generators for the automorphism group of `L`. If `ambient_representation == true` (the default), the transformations are represented with respect to the ambient space of `L`. Otherwise, the transformations are represented with respect to the (pseudo-)basis of `L`.

Setting the parameters `depth` and `bacher_depth` to a positive value may improve performance. If set to `-1` (default), the used value of `depth` is chosen heuristically depending on the rank of `L`. By default, `bacher_depth` is set to `0`.
