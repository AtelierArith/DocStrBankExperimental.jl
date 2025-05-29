```
Field(location, path, name, iter;
      grid = nothing,
      architecture = nothing,
      indices = (:, :, :),
      boundary_conditions = nothing,
      reader_kw = NamedTuple())
```

Load a field called `name` saved in a JLD2 file at `path` at `iter`ation. Unless specified, the `grid` is loaded from `path`.
