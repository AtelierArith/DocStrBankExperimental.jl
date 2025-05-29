```
get_data_reshaped(data_array::VTKDataArray; cell_data=false)
```

Retrieve actual data from a `VTKDataArray` and reshape it as 1D, 2D, or 3D arrays, in case we deal with structured grids. Note that vectors or tensors will have their components stored in the first dimension of the array. As there is no way to automatically tell from the VTK file format whether it is a tensor, the user has to reshape this manually.
