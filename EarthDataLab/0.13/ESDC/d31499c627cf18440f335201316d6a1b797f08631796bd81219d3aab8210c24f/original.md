```
function esdd(;kwargs...)
```

Opens a datacube from the AWS as a Dataset. This works on any system, but might involve some latency depending on connection speed. One can either specify a `bucket` and `store` or pick a resolution, chunking and cube region.

### Keyword arguments

  * `bucket=nothing` specify an OBS bucket for example "obs-esdc-v2.0.0"
  * `store=""` specify the root path of the cube, for example "esdc-8d-0.25deg-184x90x90-2.0.0.zarr"
  * `res="low"` pick a datacube resolution (`"low"` or `"high"` for v2 or `"low"` or `"tiny"` for v3)
  * `chunks="ts"` choose a chunking (`"ts"` for time series access or `"map"` for spatial analyses)
  * `region="global"` choose a datacube (either `"global"` or `"Colombia"`), works only for esdc v2
  * `version=3`
