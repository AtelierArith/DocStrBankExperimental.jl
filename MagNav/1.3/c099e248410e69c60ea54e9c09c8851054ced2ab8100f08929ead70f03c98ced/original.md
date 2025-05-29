```
MapV{T2 <: AbstractFloat} <: Map{T2}
```

Vector magnetic anomaly map struct. Subtype of `Map`.

| **Field** | **Type**     | **Description**                                     |
|:--------- |:------------ |:--------------------------------------------------- |
| `info`    | String       | map information                                     |
| `mapX`    | Matrix{`T2`} | `ny` x `nx` x-direction magnetic anomaly map [nT]   |
| `mapY`    | Matrix{`T2`} | `ny` x `nx` y-direction magnetic anomaly map [nT]   |
| `mapZ`    | Matrix{`T2`} | `ny` x `nx` z-direction magnetic anomaly map [nT]   |
| `xx`      | Vector{`T2`} | `nx` map x-direction (longitude) coordinates [rad]  |
| `yy`      | Vector{`T2`} | `ny` map y-direction (latitude)  coordinates [rad]  |
| `alt`     | `T2`         | map altitude [m]                                    |
| `mask`    | BitMatrix    | `ny` x `nx` mask for valid (not filled-in) map data |
