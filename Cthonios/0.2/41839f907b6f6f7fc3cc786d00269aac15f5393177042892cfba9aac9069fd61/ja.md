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

設計パラメータ（座標、時間、境界条件値、プロパティ状態変数、およびいくつかのスクラッチ配列）用の目的関数パラメータの型。
