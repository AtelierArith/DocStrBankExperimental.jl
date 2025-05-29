```julia
elementbarycenter(
    mesh::MinFEM.Mesh,
    element::Int64
) -> Vector{Float64}

```

指定されたメッシュ内の指定された要素の重心を返します。
