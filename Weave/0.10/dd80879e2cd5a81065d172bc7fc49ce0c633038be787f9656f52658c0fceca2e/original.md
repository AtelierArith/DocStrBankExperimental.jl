```
set_chunk_defaults!(k, v)
set_chunk_defaults!(kv::Pair...)
set_chunk_defaults!(opts::AbstractDict)
```

Set default options for code chunks, use [`get_chunk_defaults`](@ref) to see the current values.

E.g.: all the three examples below will set default `dpi` to `200` and `fig_width` to `8`:

  * `set_chunk_defaults!(:dpi, 200); set_chunk_defaults!(:fig_width, 8)`
  * `set_chunk_defaults!(:dpi => 200, :fig_width => 8)`
  * `set_chunk_defaults!(Dict(:dpi => 200, :fig_width => 8))`
