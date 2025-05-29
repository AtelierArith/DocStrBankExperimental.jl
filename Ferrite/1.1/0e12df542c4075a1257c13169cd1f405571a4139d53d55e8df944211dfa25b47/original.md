```
FacetQuadratureRule{shape}([::Type{T},] [quad_rule_type::Symbol,] order::Int)
FacetQuadratureRule{shape}(facet_rules::NTuple{<:Any, <:QuadratureRule{shape}})
FacetQuadratureRule{shape}(facet_rules::AbstractVector{<:QuadratureRule{shape}})
```

Create a `FacetQuadratureRule` used for integration of the facets of the refshape `shape` (of type [`AbstractRefShape`](@ref)). `order` is the order of the quadrature rule. If no symbol is provided, the default `quad_rule_type` for each facet's reference shape is used (see [QuadratureRule](@ref)). For non-default `quad_rule_type`s on cells with mixed facet types (e.g. `RefPrism` and `RefPyramid`), the `facet_rules` must be provided explicitly.

`FacetQuadratureRule` is used as one of the components to create [`FacetValues`](@ref).
