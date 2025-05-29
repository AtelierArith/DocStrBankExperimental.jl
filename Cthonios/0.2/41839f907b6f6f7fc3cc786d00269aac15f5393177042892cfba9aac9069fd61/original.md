```julia
struct ObjectiveParameters{U1, T, B, N, S, P, U3, V1, U4, Q, IC} <: Cthonios.AbstractObjectiveParameters
```

  * `X::Any`
  * `t::Any`
  * `Ubc::Any`
  * `nbc::Any`
  * `state_old::Any`
  * `state_new::Any`
  * `props::Any`
  * `grad_scratch::Any`
  * `grad_vec_scratch::Any`
  * `hvp_scratch::Any`
  * `q_vals_scratch::Any`
  * `integrator_cache::Any`

Type for objective function parameters for design parameters such as coordinates, time, bc values, properties state variables, and some scratch arrays.
