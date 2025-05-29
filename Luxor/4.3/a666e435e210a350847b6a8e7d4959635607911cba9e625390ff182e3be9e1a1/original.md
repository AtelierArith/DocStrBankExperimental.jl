```
squirclepath(cpos, w, h;
    action = :none,
    kappa = 0.75,
    reversepath = false)
```

Make a squircle or superellipse (basically a rectangle with rounded corners). Specify the center position, width, and height. 

`kappa` is a value (usually between 0 and 1) that determines the circularity of the shape. If `kappa` is `4.0 * (sqrt(2.0) - 1.0) / 3.0` (ie `0.5522847498307936`), the shape is a resonable approximation to a circle. 

Use the `reversepath` option to construct the path in the opposite direction.

The difference betweeen `squircle()` and `squirclepath()` is that the former builds polygons from points, the latter uses Bezier curves to build paths. 

See also `circlepath()`.
