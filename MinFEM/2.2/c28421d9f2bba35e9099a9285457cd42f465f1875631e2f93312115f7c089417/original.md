```
open_vtkfile_boundary(
    mesh::Mesh,
    file_name::String;
    boundary = Set{Boundary}()
)
```

Open a new VTK output file and write the mesh data into it.
