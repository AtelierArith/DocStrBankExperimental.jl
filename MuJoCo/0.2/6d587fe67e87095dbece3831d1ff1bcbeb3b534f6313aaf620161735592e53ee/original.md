```
mj_multiRay(m, d, pnt, vec, geomgroup, flg_static, bodyexclude, geomid, dist, nray, cutoff)
```

Intersect multiple rays emanating from a single point. Similar semantics to mj_ray, but vec is an array of (nray x 3) directions.

# Arguments

  * **`m::Model`** -> Constant.
  * **`d::Data`**
  * **`pnt::Vector{Float64}`** -> A vector of size 3. `pnt` should be a vector of size 3. Constant.
  * **`vec::Vector{Float64}`** -> A vector of variable size. `vec` should be a vector, not a matrix. `vec` should be of size 3*nray. Constant.
  * **`geomgroup::Vector{UInt8}`** -> An **optional** vector of size 6. `geomgroup` should be a vector of size 6. Can set to `nothing` if not required. Constant.
  * **`flg_static::UInt8`**
  * **`bodyexclude::Int32`**
  * **`geomid::Vector{Int32}`** -> A vector of variable size. `geomid` should be a vector, not a matrix. dist and `geomid` should be of size nray.
  * **`dist::Vector{Float64}`** -> A vector of variable size. `dist` should be a vector, not a matrix. `dist` and geomid should be of size nray.
  * **`nray::Int32`**
  * **`cutoff::Float64`**
