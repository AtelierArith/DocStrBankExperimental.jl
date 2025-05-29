```
MapSd{T2 <: AbstractFloat} <: Map{T2}
```

Scalar magnetic anomaly map struct used to store an additional altitude map for drape maps. Subtype of `Map`.

| **Field** | **Type**     | **Description**                                     |
|:--------- |:------------ |:--------------------------------------------------- |
| `info`    | String       | map information                                     |
| `map`     | Matrix{`T2`} | `ny` x `nx` scalar magnetic anomaly map [nT]        |
| `xx`      | Vector{`T2`} | `nx` map x-direction (longitude) coordinates [rad]  |
| `yy`      | Vector{`T2`} | `ny` map y-direction (latitude)  coordinates [rad]  |
| `alt`     | Matrix{`T2`} | `ny` x `nx` altitude map [m]                        |
| `mask`    | BitMatrix    | `ny` x `nx` mask for valid (not filled-in) map data |
