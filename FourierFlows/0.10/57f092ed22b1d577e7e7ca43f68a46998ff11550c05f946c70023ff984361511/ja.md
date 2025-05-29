```
device_array(device::Device)
device_array(device::Device, T, dim)
```

`device`に応じた適切な配列タイプを返します。すなわち、CPUの場合は`Array`、GPUの場合は`CuArray`です。
