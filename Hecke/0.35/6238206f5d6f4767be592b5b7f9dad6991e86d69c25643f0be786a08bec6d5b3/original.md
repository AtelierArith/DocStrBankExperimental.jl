```
getindex(T::TorQuadModule, i::Int) -> TorQuadModuleElem
```

Return the `i`-th generator of `T`.

This is equivalent to `gens(T)[i]`.

# Example

```jldoctest
julia> R = rescale(root_lattice(:D,4),2);

julia> D = discriminant_group(R);

julia> D[1]
Element
  of finite quadratic module: (Z/2)^2 x (Z/4)^2 -> Q/2Z
with components [1 0 0 0]

julia> D[2]
Element
  of finite quadratic module: (Z/2)^2 x (Z/4)^2 -> Q/2Z
with components [0 1 0 0]
```
