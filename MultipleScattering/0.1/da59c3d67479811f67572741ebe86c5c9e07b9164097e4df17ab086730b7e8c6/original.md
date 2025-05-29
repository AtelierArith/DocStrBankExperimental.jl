```
points_in_shape(Shape; resolution = 20, xres = resolution, yres = resolution,
         exclude_region = EmptyShape(region), kws...)
```

returns `(x_vec, region_inds)` where `x_vec` is a vector of points that cover a box which bounds `Shape`, and `region_inds` is an array of linear indices such that `x_vec[region_inds]` are points contained `Shape`. For 3D we use `zres` instead of `yres`.
