```
MapS3D{T2 <: AbstractFloat} <: Map{T2}
```

3D (multi-level) scalar magnetic anomaly map struct. Subtype of `Map`.

| **Field** | **Type**      | **Description**                                                      |
|:--------- |:------------- |:-------------------------------------------------------------------- |
| `info`    | String        | map information                                                      |
| `map`     | Array{`T2,3`} | `ny` x `nx` x `nz` 3D (multi-level) scalar magnetic anomaly map [nT] |
| `xx`      | Vector{`T2`}  | `nx` map x-direction (longitude) coordinates [rad]                   |
| `yy`      | Vector{`T2`}  | `ny` map y-direction (latitude)  coordinates [rad]                   |
| `alt`     | Vector{`T2`}  | `nz` map altitude levels [m]                                         |
| `mask`    | BitArray{3}   | `ny` x `nx` x `nz` mask for valid (not filled-in) map data           |
