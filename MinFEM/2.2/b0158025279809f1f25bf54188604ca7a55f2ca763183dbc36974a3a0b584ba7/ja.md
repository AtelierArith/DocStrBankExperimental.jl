```
quadrature_points_boundary(
    mesh::Mesh,
    order::Int64;
    boundaryElements::Set{Int64} = Set{Int64}()
)-> Array{Array{Float64,1},1}
```

与えられたメッシュ内の各境界要素におけるガウス・レジェンドルの積分点のグローバル座標を返します。これは、指定された次数までの多項式の正確な積分のためです。
