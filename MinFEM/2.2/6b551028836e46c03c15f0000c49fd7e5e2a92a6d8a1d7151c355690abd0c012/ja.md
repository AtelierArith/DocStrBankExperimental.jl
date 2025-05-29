```julia
select_domains(
    mesh::MinFEM.Mesh,
    args...
) -> Set{MinFEM.Domain}

```

メッシュのすべてまたは指定された物理境界のセットを返します。
