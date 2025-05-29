```
TwoSidedFixedLimit(h::Float64)
```

Classical fixed two-sided limit, such that the run length $RL$ of a control chart is the first time $t$ in which the statistic $C_t$ crosses the limit:

$RL = \inf\{t > 0 : |C_t| > h\}$.

Note that by definition, $h > 0$.
