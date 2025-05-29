```
DimArray(x, names...)
DimArray(x, names..., maps...)
```

Interprets symbols & strings as dimension names (in order), and numbers, functions & dictionaries as index maps (for each dimension). Numbers are converted to functions `i -> i*n` to indicate e.g. that we have every n-th data point. The `ndims(x)+1`-th name (if given) is equivalent to keyword `label=name`, labelling what the elements of `x` mean. Giving too few names/maps is no problem, too many will give a warning.
