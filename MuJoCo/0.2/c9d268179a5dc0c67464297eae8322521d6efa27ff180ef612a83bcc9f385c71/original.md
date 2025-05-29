```
mj_geomDistance(m, d, geom1, geom2, distmax, fromto)
```

Returns smallest signed distance between two geoms and optionally segment from geom1 to geom2.

# Arguments

  * **`m::Model`** -> Constant.
  * **`d::Data`** -> Constant.
  * **`geom1::Int32`**
  * **`geom2::Int32`**
  * **`distmax::Float64`**
  * **`fromto::Matrix{Float64}`** -> An **optional** matrix of variable size. `fromto` should be of size 6. Can set to `nothing` if not required.
