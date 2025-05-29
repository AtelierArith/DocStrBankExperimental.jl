```
getscale(R::Matrix)
getscale()
```

Get the current scale of a 3x3 matrix, or the current Luxor scale.

Returns a tuple of x and y values.

```julia-repl
julia> getscale()
(1.0, 1.0)
```

See `getmatrix()` for details.
