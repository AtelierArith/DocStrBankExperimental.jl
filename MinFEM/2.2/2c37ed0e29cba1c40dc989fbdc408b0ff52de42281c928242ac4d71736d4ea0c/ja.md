```julia
quadrature_points_boundary(
    element::Int64,
    mesh::MinFEM.Mesh,
    order::Int64
) -> Vector{Vector{Float64}}

```

指定されたメッシュ内の境界要素に対するガウス・レジェンドルの数値積分点のグローバル座標を返します。これは、与えられた次数までの多項式の正確な積分のためです。
