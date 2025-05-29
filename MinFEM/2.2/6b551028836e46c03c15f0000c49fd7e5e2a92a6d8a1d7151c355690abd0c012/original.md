```julia
select_domains(
    mesh::MinFEM.Mesh,
    args...
) -> Set{MinFEM.Domain}

```

Returns set of all or specified physical boundaries of the mesh.
