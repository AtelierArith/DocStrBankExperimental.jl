```
dispatch(Pnl_req, Pbatt_cmax, Pbatt_dmax, Pgen_max)
```

Return the dispatch decision for a rule-based strategy.

# Arguments

  * `Pnl_req`: the requested load at time t.
  * `Pbatt_cmax`: the maximum battery charge power at time t.
  * `Pbatt_dmax`: the maximum battery discharge power at time t.
  * `Pgen_max`: the diesel generator rated power.
