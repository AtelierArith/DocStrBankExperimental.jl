```
arraytype(grid::Grid)
```

Return the array type corresponding to data that lives on `grid`. Defaults to `Array`. New data types (for example, grids that exist on GPUs) must implement new array types.
