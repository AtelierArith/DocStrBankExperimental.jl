```
ALNS(sol::Solution, meths_ch, meths_de, meths_re; 
    meths_compat, consider_initial_sol, scheduler_params, lns_params, alns_params)
```

Create an Adaptive Large Neighborhood Search (ALNS).

Create an ALNS, i.e., LNS with `ALNSMethodSelector``for the given solution with  the given construction, and repair methods provided as`Vector{MHMethod}`. If`consider*initial*sol`, consider the given solution as valid initial solution; otherwise it is assumed to be uninitialized.
