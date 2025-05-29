```julia
nc_read(file; ...) -> Any
nc_read(
    file,
    band;
    type,
    period,
    ind,
    raw,
    nodata,
    verbose
) -> Any

```

# Arguments

  * `band`  : string (variable name) or int (band id). If `int` provided,            `bandName = nc_bands(file)[band]`
  * `type`  : returned data type, e.g. `Float32`
  * `period`: `[year_start, year_end]` or `year`, time should be in the 3rd dimension.
  * `ind`   : If `ind` provided, `period` will be ignored.
  * `raw`   : Boolean. 

      * `true`: raw data.
      * `false` (default): `missing` will be replaced with `nodata`
  * `verbose`: Boolean. It `true`, `data` and `ind` will be printed on the console.
