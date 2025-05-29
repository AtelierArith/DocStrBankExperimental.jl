```
pointgroup(iuclab::String, ::Union{Val{D}, Integer}=Val(3))  -->  PointGroup{D}
```

Return the symmetry operations associated with the point group identified with label `iuclab` in dimension `D` as a `PointGroup{D}`.
