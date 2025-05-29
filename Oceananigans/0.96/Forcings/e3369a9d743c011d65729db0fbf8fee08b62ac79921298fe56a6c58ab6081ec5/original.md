```
Forcing(array::AbstractArray)
```

Return a `Forcing` by `array`, which can be added to the tendency of a model field.

Forcing is computed by calling `array[i, j, k]`, so `array` must be 3D with `size(grid)`.
