```
update_matrix(data::DataMatrix, matrix, model=nothing;
              var::Union{Symbol,String,DataFrame} = "",
              obs::Union{Symbol,String,DataFrame} = "")
```

Create a new `DataMatrix` by replacing parts of `data` with new values. Mostly useful when implementing new `ProjectionModel`s.

  * `matrix` - the new matrix.
  * `model` - will be appended to the list of models from `data`. If set to `nothing`, the resulting list of `models` will be empty.

Kwargs:

  * `var` - One of:

      * `:copy` - Copy from `data`.
      * `:keep` - Share `var` with `data`.
      * `::DataFrame` - Replace with a new table with variable annotations.
      * `prefix::String` - Prefix, the new variables will be named prefix1, prefix2, etc.
  * `obs` See `var`.
