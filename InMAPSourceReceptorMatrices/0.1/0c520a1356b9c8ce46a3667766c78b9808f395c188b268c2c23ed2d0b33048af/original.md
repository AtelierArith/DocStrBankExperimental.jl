```
run_sr(source_emis::DataFrame, [cell_variables]) -> receptor_emis::DataFrame
```

Runs the source receptor matrix for the given source emissions, where each row represents an emitter.  Note that `source_emis` must have the following columns:

  * `latitude <: Number` - latitude of the source
  * `longitude <: Number` - longitude of the source
  * `layer_idx <: Integer` - layer index ∈ {1,2,3}, for effective emission heights at ground level (emissions between 0 and 57 m), low level (57–379 m), and high level (>379 m) respectively
  * `<emis_type> <: Number` - the average emissions rate, in μg / s, for emission type `<emis_type>` ∈ `{PM2_5, NOx, SO2, VOC, NH3}`.  There can be between 1 and 5 of these columns.
  * (optional) `source_idx <: Int64` - which grid cell index corresponds to the source.  If given, `latitude` and `longitude` no longer used.

Returns the `receptor_emis` table which contains columns for each of the PM types created by the source emissions, as well as columns for each of the variables in `cell_variables`, and a column for `geometry_longlat`, which contains the `(lon, lat)` geometry of each grid cell.
