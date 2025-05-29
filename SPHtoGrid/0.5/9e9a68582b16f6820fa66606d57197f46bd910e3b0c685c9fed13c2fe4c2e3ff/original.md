```
write_vtk_image(filename::String, image::Array{<:Real},
                image_name::String, par::mappingParameters;
                units::String = "[i.u.]", snap::Integer = 0)
```

Writes a mapped image to a vti file.
