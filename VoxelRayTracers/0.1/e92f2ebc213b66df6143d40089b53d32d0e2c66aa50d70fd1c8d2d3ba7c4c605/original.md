```
hits = eachtraversal(ray, edges)
```

Compute the traversal of `ray` through a grid that is the produce of `edges`.

# Example

```jldoctest
julia> using VoxelRayTracers

julia> edges = (0:1:10, 4:2:10,);

julia> ray = (position=[0,0], velocity=[1,1]);

julia> for hit in eachtraversal(ray, edges)
           println(hit)
       end
(voxelindex = CartesianIndex(5, 1), entry_time = 4.0, exit_time = 5.0)
(voxelindex = CartesianIndex(6, 1), entry_time = 5.0, exit_time = 6.0)
(voxelindex = CartesianIndex(7, 2), entry_time = 6.0, exit_time = 7.0)
(voxelindex = CartesianIndex(8, 2), entry_time = 7.0, exit_time = 8.0)
(voxelindex = CartesianIndex(9, 3), entry_time = 8.0, exit_time = 9.0)
(voxelindex = CartesianIndex(10, 3), entry_time = 9.0, exit_time = 10.0)
```
