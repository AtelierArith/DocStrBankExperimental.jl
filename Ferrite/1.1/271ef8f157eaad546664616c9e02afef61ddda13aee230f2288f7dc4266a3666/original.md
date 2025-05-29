```
evaluate_at_points(ph::PointEvalHandler, dh::AbstractDofHandler, dof_values::Vector{T}, [fieldname::Symbol]) where T
evaluate_at_points(ph::PointEvalHandler, proj::L2Projector, dof_values::Vector{T}) where T
```

Return a `Vector{T}` (for a 1-dimensional field) or a `Vector{Vec{fielddim, T}}` (for a vector field) with the field values of field `fieldname` in the points of the `PointEvalHandler`. The `fieldname` can be omitted if only one field is stored in `dh`. The field values are computed based on the `dof_values` and interpolated to the local coordinates by the function interpolation of the corresponding `field` stored in the `AbstractDofHandler` or the `L2Projector`.

Points that could not be found in the domain when constructing the `PointEvalHandler` will have `NaN`s for the corresponding entries in the output vector.
