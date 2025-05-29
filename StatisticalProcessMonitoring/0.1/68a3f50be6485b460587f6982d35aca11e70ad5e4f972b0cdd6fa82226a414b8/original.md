```
OneSidedCurvedLimit(h::Float64, upw::Bool)
OneSidedCurvedLimit(h::Vector{T}, upw::Vector{Bool})
```

Curved one-sided limit, such that the run length $RL$ of a control chart is the first time $t$ in which the statistic $C_t$ crosses the limit.

  * if `upw == true`, $RL = \inf\{t : C_t > h\cdot f(t)\}$
  * if `upw == false`, $RL = \inf\{t : C_t < -h\cdot f(t)\}$

Note that by definition, $h > 0$.
