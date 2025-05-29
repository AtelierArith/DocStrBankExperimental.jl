```
write_opf(file, opf)
```

Write an MTG with explicit geometry to disk as an OPF file.

# Notes

Node attribute `:geometry` is treated as a reserved keyword and should not be used without knowing their meaning.

# Examples

```julia
using PlantGeom
file = joinpath(dirname(dirname(pathof(PlantGeom))),"test","files","simple_plant.opf")
opf = read_opf(file)
write_opf("test.opf", opf)
opf2 = read_opf("test.opf")
viz(opf2)
```
