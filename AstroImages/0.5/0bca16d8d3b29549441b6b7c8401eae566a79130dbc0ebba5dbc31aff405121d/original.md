```
Percent(99.5)
```

Returns a callable that calculates display limits that include the given percent of the image data. Reproduces the behaviour of the SAO DS9 scale menu.

Example:

```julia-repl
julia> imview(img, clims=Percent(90))
```

This will set the limits to be the 5th percentile to the 95th percentile.
