```julia
outernormalvector(
    mesh::MinFEM.Mesh,
    boundaryElement::Int64,
    J::AbstractMatrix{Float64}
) -> Any

```

Returns the outer normal vector at a boundary element of the given mesh using a pre-computed jacobian transformation matrix of the parent element.
