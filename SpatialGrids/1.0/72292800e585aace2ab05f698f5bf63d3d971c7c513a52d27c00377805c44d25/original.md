```
SparseVoxelGrid(points, voxel_size)
SparseVoxelGrid(points, voxel_size::NTuple{3, AbstractFloat})
```

Creates a sparse spatial grid by organising 3D points into voxels. `points` can either be a 3xN matrix or a `PointCloud`. `voxel_size` will either create uniformly sized voxels in each axis or if it is a 3D tuple the size of each axis can be specified.

### Example

To create a spatial grid with voxel side length of 10 metres for arbitrary points:

```julia
using PointClouds
points = rand(3, 100000) * 20.0
grid = SparseVoxelGrid(points, 10.0)
```

The created grid is an iteratable object which returns a `Voxel` in each iteration. Each voxel can be accessed directly with a `for` loop or all voxels can be `collect`ed into an array. Likewise, the returned `Voxel` is an iterable object that returns the point indices:

```julia
# Iterate through each voxel in grid
for voxel in grid
    # Get each point index in voxel
    for idx in voxel
        # Do stuff with points[:,idx]
    end
    # Or, you may want all point indices in a voxel
    all_point_indices = collect(voxel)
end
```
