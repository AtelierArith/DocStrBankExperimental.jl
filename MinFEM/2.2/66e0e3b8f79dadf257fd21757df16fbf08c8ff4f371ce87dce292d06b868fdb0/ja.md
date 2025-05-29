```julia
outernormalvector(
    mesh::MinFEM.Mesh,
    boundaryElement::Int64
) -> Vector{Float64}

```

指定されたメッシュの指定された境界要素における外法線ベクトルを返します。
