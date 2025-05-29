```
getmultiplicity(r::ElemRestriction)
```

Convenience function to get the multiplicity of nodes in the [`ElemRestriction`](@ref), where the result is returned in a newly allocated Julia `Vector{CeedScalar}` (see also [`getmultiplicity!`](@ref)).
