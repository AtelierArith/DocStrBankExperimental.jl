```
PendulumEnv(;kwargs...)
```

# キーワード引数

  * `T = Float64`
  * `max_speed = T(8)`
  * `max_torque = T(2)`
  * `g = T(10)`
  * `m = T(1)`
  * `l = T(1)`
  * `dt = T(0.05)`
  * `max_steps = 200`
  * `continuous::Bool = true`
  * `n_actions::Int = 3`
  * `rng = Random.default_rng()`
