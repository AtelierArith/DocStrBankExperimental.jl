compose!(m::DAMap, m2::DAMap, m1::DAMap; keep*scalar::Bool=true, work*ref::Union{Nothing,Vector{<:Union{Float64,ComplexF64}}}=nothing, dospin::Bool=true, work*prom::Union{Nothing,Tuple{Vararg{Vector{<:ComplexTPS64}}}}=prep*comp*work*prom(m,m2,m1))

In-place `DAMap` composition which calculates `m = m2 ∘ m1`, ignoring the scalar part of `m1`.

Aliasing `m === m2` is allowed, but NOT `m === m1`. `m2 === m1` is fine. The destination map `m` should be  properly set up (with correct types promoted if necessary), and have `m.x[1:nv]` (and `m.Q` if spin)  containing allocated TPSs.

If `keep_scalar` is set to `true`, then the scalar part of `m1` is retained. In this case, a temporary  vector `work_ref` must be used to store the scalar part before calling the low-level `compose_it!`,  then added back into `m1` after composition. `work_ref` can be optionally provided, or will be created  internally in this case. Default is `true`.

If `dospin` is `true`, then the quaternion part of the maps will be composed as well. Default is `true`.

See the documentation for `compose_it!` for information on `work_prom`.

### Keyword Arguments

  * `keep_scalar` – Specify whether to keep the scalar part in `m1` or throw it away. If `true`, a temporary vector storing the scalar part must be used. Default is true
  * `work_ref` – If `keep_scalar` is true, the temporary vector can be provided in this keyword argument. If `nothing` is provided, the temporary will be created internally. Default is `nothing`
  * `dospin` – Specify whether or not to include the quaternions in the concatenation. Default is `true`
  * `work_prom` – Temporary vector of allocated `ComplexTPS64`s when there is implicit promotion. See the `compose_it!` documentation for more details. Default is output from `prep_comp_work_prom(m, m2, m1)`
