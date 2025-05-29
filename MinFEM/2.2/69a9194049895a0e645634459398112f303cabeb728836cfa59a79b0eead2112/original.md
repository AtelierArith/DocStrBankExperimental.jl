```julia
open_vtkfile_boundary(
    mesh::MinFEM.Mesh,
    file_name::String,
    boundaryElements::Set{Int64}
) -> WriteVTK.DatasetFile

```

Open a new VTK output file and write the mesh data into it.
