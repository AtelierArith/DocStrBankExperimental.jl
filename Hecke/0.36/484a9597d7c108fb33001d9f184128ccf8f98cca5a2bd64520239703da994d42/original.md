```
is_isometric_with_isometry(L::AbstractLat, M::AbstractLat; ambient_representation::Bool = true
                                                           depth::Int = -1, bacher_depth::Int = 0)
                                                          -> (Bool, MatElem)
```

Return whether the lattices `L` and `M` are isometric. If this is the case, the second returned value is an isometry `T` from `L` to `M`.

By default, that isometry is represented with respect to the bases of the ambient spaces, that is, $T V_M T^t = V_L$ where $V_L$ and $V_M$ are the Gram matrices of the ambient spaces of `L` and `M` respectively. If `ambient_representation == false`, then the isometry is represented with respect to the (pseudo-)bases of `L` and `M`, that is, $T G_M T^t = G_L$ where $G_M$ and $G_L$ are the Gram matrices of the (pseudo-)bases of `L` and `M` respectively.

Setting the parameters `depth` and `bacher_depth` to a positive value may improve performance. If set to `-1` (default), the used value of `depth` is chosen heuristically depending on the rank of `L`. By default, `bacher_depth` is set to `0`.
