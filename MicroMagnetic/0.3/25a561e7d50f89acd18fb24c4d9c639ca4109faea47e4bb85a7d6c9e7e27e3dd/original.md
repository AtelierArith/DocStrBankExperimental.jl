```
save_vtk(mesh::Mesh, shape::Union{CSGNode,Shape}, fname::String)
```

Save the shape to vtk. 

```julia
    mesh = FDMesh(dx=2e-9, dy=2e-9, dz=2e-9, nx=100, ny=100, nz=50)
    t1 = Torus(R = 60e-9, r=20e-9)
    save_vtk(mesh, t1, "torus")
```
