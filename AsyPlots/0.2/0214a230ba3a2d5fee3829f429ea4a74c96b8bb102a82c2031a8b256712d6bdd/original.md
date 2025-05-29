```
Path3D(points;label="",pen=Pen(),arrow="",spline=false)
```

A graphics primitive representing a two-dimensional path

`points` may be an Array of `Vec3`s or an Array of 3-tuples. Alternatively, iterables of coordinates may be supplied separately as `x` and `y`

# Examples

```julia-repl
julia> Path3D([(0,0),(1,0),(1,1)];pen="MidnightBlue")
```
