```
LNS(sol::Solution, meths_ch, meths_de, meths_re;
    meths_compat, consider_initial_sol, scheduler_params, 
    method_selector, params)
```

Create a LNS.

Create a LNS for the given solution with the given construction, and repair methods provided as `Vector{MHMethod}`. If `consider_initial_sol`, consider the given solution as valid initial solution; otherwise it is assumed to be uninitialized.
