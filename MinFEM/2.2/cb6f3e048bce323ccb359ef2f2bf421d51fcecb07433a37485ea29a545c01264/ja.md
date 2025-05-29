```julia
select_boundaries(
    mesh::MinFEM.Mesh,
    args...
) -> Set{MinFEM.Boundary}

```

メッシュのすべてまたは指定された物理境界のセットを返します。
