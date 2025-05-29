```
mj_getState(m, d, state, spec)
```

Get state.

# Arguments

  * **`m::Model`** -> Constant.
  * **`d::Data`** -> Constant.
  * **`state::Vector{Float64}`** -> A vector of variable size. `state` should be a vector, not a matrix. `state` size should equal mj_stateSize(m, spec).
  * **`spec::Int32`**
