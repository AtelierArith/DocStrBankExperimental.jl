```
device_array(device::Device)
device_array(device::Device, T, dim)
```

Return the proper array type according to the `device`, i.e., `Array` for CPU and `CuArray` for GPU.
