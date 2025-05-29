```
MapS{T2 <: AbstractFloat} <: Map{T2}
```

Scalar magnetic anomaly map struct. Subtype of `Map`.

| **Field** | **Type**     | **Description**                                     |
|:--------- |:------------ |:--------------------------------------------------- |
| `info`    | String       | map information                                     |
| `map`     | Matrix{`T2`} | `ny` x `nx` scalar magnetic anomaly map [nT]        |
| `xx`      | Vector{`T2`} | `nx` map x-direction (longitude) coordinates [rad]  |
| `yy`      | Vector{`T2`} | `ny` map y-direction (latitude)  coordinates [rad]  |
| `alt`     | `T2`         | map altitude [m]                                    |
| `mask`    | BitMatrix    | `ny` x `nx` mask for valid (not filled-in) map data |
