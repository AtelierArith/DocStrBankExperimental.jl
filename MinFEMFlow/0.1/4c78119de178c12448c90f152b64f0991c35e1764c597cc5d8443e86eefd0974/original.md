```julia
assemble_saddlepointmatrix_stokes(
    mesh::MinFEM.Mesh;
    alpha
) -> Any

```

Returns saddle point system matrix including inf-sup stabilization for the solution of the discretized Stokes equation. 
