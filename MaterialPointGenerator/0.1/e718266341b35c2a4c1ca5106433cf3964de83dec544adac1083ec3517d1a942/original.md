```
polygon2particle(stl_file, msh_file, output_file, nid_file, h; verbose=true)
```

## Description:

Generate structured particles from a given `.stl` file and `.msh` file. The particles are generated by voxelizing the 2D space of the STL model. The voxel size `h` should be positive.
