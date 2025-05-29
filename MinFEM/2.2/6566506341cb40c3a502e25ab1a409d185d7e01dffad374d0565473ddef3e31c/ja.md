```
outernormalvector(
    mesh::Mesh;
    boundaryElements::Set{Int64} = Set{Int64}()
) -> Vector{Float64}
```

与えられたメッシュのすべてまたは指定された境界要素における外法線ベクトルの係数ベクトルを返します。
