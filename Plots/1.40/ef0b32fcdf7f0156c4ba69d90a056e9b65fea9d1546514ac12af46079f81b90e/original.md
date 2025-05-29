```
path3d(x,y,z)
path3d!(x,y,z)
```

Plot a 3D path from `(x[1],y[1],z[1])` to `(x[2],y[2],z[2])`, ..., to `(x[end],y[end],z[end])`.

# Example

```julia-repl
julia> path3d([0,1,2,3],[0,1,4,9],[0,1,8,27])
```
