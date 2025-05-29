```
X,Y,Z = xyz_grid(X_vec::Any, Y_vec::Any, Z_vec::Any)
```

Creates a `X,Y,Z` grid. It works just as `lonlatdepth_grid` apart from the better suited name.

# Example 1: Create 3D grid

```julia-repl
julia> X,Y,Z =  xyz_grid(10:20,30:40,(-10:-1)km);
julia> size(X)
(11, 11, 10)
```

See `lonlatdepth_grid` for more examples.
