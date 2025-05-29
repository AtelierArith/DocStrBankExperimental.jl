```
polyhedron2particle(stl_file::String, output_file, h; method::String="voxel", 
    verbose::Bool=false)
```

## Description:

Convert a polyhedron (`.stl`) to a set of particles. The function will write the populated  particles of each voxel into a `.xyz` file. The voxel size is defined by `h`, it is suggest to be equal to the MPM background grid size. `method` can be "voxel" or "ray" in string.The  `verbose` is a flag to show the time consumption of each step.

## Example:

```julia
stl_file = "/path/to/your/model.stl"
output_file = "/path/to/your/model.xyz"
h = 0.1
polyhedron2particle(stl_file, output_file, h, verbose=true)
```
