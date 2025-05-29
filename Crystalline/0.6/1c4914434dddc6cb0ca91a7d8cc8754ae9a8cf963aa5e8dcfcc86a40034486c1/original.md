```
pointgroup(pgnum::Integer, ::Union{Val{D}, Integer}=Val(3), setting::Integer=1)
                                                                  -->  PointGroup{D}
```

Return the symmetry operations associated with the point group identfied with canonical number `pgnum` in dimension `D` as a `PointGroup{D}`. The connection between a point group's numbering and its IUC label is enumerated in `Crystalline.PG_NUM2IUC[D]` and `Crystalline.IUC2NUM[D]`.

Certain point groups feature in multiple setting variants: e.g., IUC labels 321 and 312 both correspond to `pgnum = 18` and correspond to the same group structure expressed in two different settings. The `setting` argument allows choosing between these setting variations.
