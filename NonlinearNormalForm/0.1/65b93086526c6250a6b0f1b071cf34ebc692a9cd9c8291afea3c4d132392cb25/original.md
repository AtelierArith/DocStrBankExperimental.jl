```
inv!(m::TaylorMap, m1::TaylorMap; dospin::Bool=true, work_ref::Union{Nothing,Vector{<:Union{Float64,ComplexF64}}}=nothing)
```

In-place inversion of the `TaylorMap` setting `m = inv(m1)`. Aliasing `m === m1` is allowed, however  in this case a temporary vector must be used to store the scalar part of `m1` prior to inversion so  that the entrance/exit coordinates of the map can be properly handled.

### Keyword Arguments

  * `dospin` – Specify whether to invert the quaternion as well, default is `true`
  * `work_ref` – If `m === m1`, then a temporary vector must be used to store the scalar part. If not provided and `m === m1`, this temporary will be created internally. Default is `nothing`
