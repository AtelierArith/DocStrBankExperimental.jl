```
write_projection(vtk::VTKGridFile, proj::L2Projector, vals::Vector, name::AbstractString)
```

`vals`を`proj`を使ってグリッドノードに投影し、`vtk`に保存します。
