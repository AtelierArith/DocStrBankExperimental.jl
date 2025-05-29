```
convert_arguments(P, x, y, f)::(Vector, Vector, Matrix)
```

Takes vectors `x` and `y` and the function `f`, and applies `f` on the grid that `x` and `y` span. This is equivalent to `f.(x, y')`. `P` is the plot Type (it is optional).
