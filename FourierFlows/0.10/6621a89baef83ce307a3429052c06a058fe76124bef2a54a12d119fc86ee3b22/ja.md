```
device_array(grid::AbstractGrid)
```

`grid`の`device`に応じた適切な配列タイプを返します。すなわち、CPUの場合は`Array`、GPUの場合は`CuArray`です。
