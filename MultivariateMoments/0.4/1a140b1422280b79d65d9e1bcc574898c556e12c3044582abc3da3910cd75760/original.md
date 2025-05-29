```
struct StaircaseDependence
    standard_or_corner::Bool
    linear::LinearDependence
end
```

Dependence of the element of a basis representing the indices of the rows of a [`MacaulayNullspace`]. If the field `standard_or_corner` is true then the elements is either standard or is a corner (depending on the linear dependence encoded in the `linear` field). Otherwise, it is a border that is not a corner or it is not even a border.  See [`LinearDependence`](@ref) for the `linear` field.
