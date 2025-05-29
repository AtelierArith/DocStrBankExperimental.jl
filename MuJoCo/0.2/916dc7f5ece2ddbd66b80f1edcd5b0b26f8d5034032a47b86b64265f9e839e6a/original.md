```
mj_ray(m, d, pnt, vec, geomgroup, flg_static, bodyexclude, geomid)
```

Intersect ray (pnt+x*vec, x>=0) with visible geoms, except geoms in bodyexclude. Return distance (x) to nearest surface, or -1 if no intersection and output geomid. geomgroup, flg_static are as in mjvOption; geomgroup==NULL skips group exclusion.

# Arguments

  * **`m::Model`** -> Constant.
  * **`d::Data`** -> Constant.
  * **`pnt::Vector{Float64}`** -> A vector of size 3. `pnt` should be a vector of size 3. Constant.
  * **`vec::Vector{Float64}`** -> A vector of size 3. `vec` should be a vector of size 3. Constant.
  * **`geomgroup::Vector{UInt8}`** -> An **optional** vector of size 6. `geomgroup` should be a vector of size 6. Can set to `nothing` if not required. Constant.
  * **`flg_static::UInt8`**
  * **`bodyexclude::Int32`**
  * **`geomid::Vector{Int32}`** -> A vector of size 1. `geomid` should be a vector of size 1.
