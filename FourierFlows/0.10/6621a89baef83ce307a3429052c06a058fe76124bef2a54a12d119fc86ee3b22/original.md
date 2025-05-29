```
device_array(grid::AbstractGrid)
```

Return the proper array type according to the `grid`'s `device`, i.e., `Array` for CPU and `CuArray` for GPU.
