```
getmultiplicity!(r::ElemRestriction, v::AbstractCeedVector)
```

Get the multiplicity of nodes in an [`ElemRestriction`](@ref). The [`CeedVector`](@ref) `v` should be an L-vector (i.e. `length(v) == getlvectorsize(r)`, see [`create_lvector`](@ref)).
