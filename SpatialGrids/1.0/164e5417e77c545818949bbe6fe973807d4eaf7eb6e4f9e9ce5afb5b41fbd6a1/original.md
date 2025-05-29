```
in_cuboid(grid::SparseVoxelGrid, voxel::Voxel, radius::Int)
in_cuboid(grid::SparseVoxelGrid, voxel_id::NTuple{3,Int}, radius::Int)
```

Search for neighbouring voxels within a `radius` around the reference `voxel` or `voxel_id`. Returns a `Voxel` in each iteration.

### Example

The `in_cuboid` function can be implemented using the `do` block syntax:

```julia
radius = 1
query_voxel = (1,1,1)
in_cuboid(grid, query_voxel, radius) do voxel
    for index in voxel
        # Do stuff with point[:, index]
    end
    # Or, collect all indices into an array
    indices = collect(voxel)
end
```

Alternatively, you may use a `for` loop which returns a voxel in each iteratation:

```julia
for voxel in in_cuboid(grid, query_voxel, radius)
    # do stuff with the `Voxel` (i.e. collect(voxel) or for index in voxel etc.)
end
```
