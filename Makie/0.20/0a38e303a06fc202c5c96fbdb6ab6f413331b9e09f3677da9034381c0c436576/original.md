```
convert_arguments(P, x, y, z, f)::(Vector, Vector, Vector, Matrix)
```

Takes `AbstractVector` `x`, `y`, and `z` and the function `f`, evaluates `f` on the volume spanned by `x`, `y` and `z`, and puts `x`, `y`, `z` and `f(x,y,z)` in a Tuple.

`P` is the plot Type (it is optional).
