```
NM(;max_episode::Int=1000, p_num::Int=10, nelder_mead=nothing, ar::Number=1.0, ae::Number=2.0, ac::Number=0.5, as0::Number=0.5, seed::Number=1234)
```

State optimization algorithm: NM.

  * `max_episode`: The number of populations.
  * `p_num`: The number of the input states.
  * `nelder_mead`: Initial guesses of the optimization variables.
  * `ar`: Reflection constant.
  * `ae`: Expansion constant.
  * `ac`: Constraction constant.
  * `as0`: Shrink constant.
