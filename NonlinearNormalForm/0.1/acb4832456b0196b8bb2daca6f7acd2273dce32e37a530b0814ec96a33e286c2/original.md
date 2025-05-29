```
compose!(m::TPSAMap, m2::TPSAMap, m1::TPSAMap; dospin::Bool=true, work_prom::Union{Nothing,Tuple{Vararg{Vector{<:ComplexTPS64}}}}=prep_comp_work_prom(m,m2,m1))
```

In-place `TPSAMap` composition which calculates `m = m2 ∘ m1`, including the scalar part of `m1`.

Aliasing `m === m2` is allowed, but NOT `m === m1`. `m2 === m1` is fine. The destination map `m` should be  properly set up (with correct types promoted if necessary), and have `m.x[1:nv]` (and `m.Q` if spin)  containing allocated TPSs.

If `dospin` is `true`, then the quaternion part of the maps will be composed as well. Default is `true`.

See the documentation for `compose_it!` for information on `work_prom`.

### Keyword Arguments

  * `dospin` – Specify whether or not to include the quaternions in the concatenation. Default is `true`
  * `work_prom` – Temporary vector of allocated `ComplexTPS64`s when there is implicit promotion. See the `compose_it!` documentation for more details. Default is output from `prep_comp_work_prom(m, m2, m1)`
