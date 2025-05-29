```
number_of_tables(outer_data, t::Symbol)
```

Number of declared tables for given type `t`. Should be one of the following:

  * `:satnum` (saturation function region)
  * `:pvtnum` (PVT function region)
  * `:eqlnum` (equilibriation region)
  * `:eosnum` (equation-of-state region)
