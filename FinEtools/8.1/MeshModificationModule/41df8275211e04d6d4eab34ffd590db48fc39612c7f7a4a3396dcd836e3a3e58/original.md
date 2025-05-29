```
mirrormesh(
    fens::FENodeSet,
    fes::ET,
    Normal::Vector{T},
    Point::Vector{T};
    kwargs...,
) where {ET<:AbstractFESet, T<:Number}
```

Mirror a mesh in a plane given by its normal and one point.

# Keyword arguments

  * `renumb` = node renumbering function for the mirrored element

Warning: The code to relies on the numbering of the finite elements: to reverse the orientation of the mirrored finite elements, the connectivity is listed in reverse order.   If the mirrored finite elements do not follow this rule (for instance hexahedra or quadrilaterals), their areas/volumes will come out negative. In such a case the renumbering function of the connectivity needs to be supplied.

For instance: H8 elements require the renumbering function to be supplied as

```
renumb = (c) -> c[[1, 4, 3, 2, 5, 8, 7, 6]]
```
