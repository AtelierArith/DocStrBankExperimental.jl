```
get_vector(M::OrthogonalMatrices, p, Xⁱ, B::DefaultOrthogonalBasis)
get_vector(M::Rotations, p, Xⁱ, B::DefaultOrthogonalBasis)
```

Convert the unique tangent vector components `Xⁱ` at point `p` on [`Rotations`](@ref) or [`OrthogonalMatrices`](@ref) to the matrix representation $X$ of the tangent vector. See [`get_coordinates`](@ref get_coordinates(::GeneralUnitaryMatrices, ::Any...)) for the conventions used.
