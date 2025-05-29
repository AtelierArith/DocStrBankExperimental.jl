```
DefaultPolicyLB(policy; max_depth=nothing, final_value=(m,x)->0.0)
DefaultPolicyLB(solver; max_depth=nothing, final_value=(m,x)->0.0)
```

A lower bound calculated by running a default policy on the scenarios in a belief.

# Keyword Arguments

  * `max_depth::Union{Nothing,Int}=nothing`: max depth to run the simulation. The depth of the belief will be automatically subtracted so simulations for the bound will be run for `max_depth-b.depth` steps. If `nothing`, the solver's max depth will be used.
  * `final_value=(m,x)->0.0`: a function (or callable object) that specifies an additional value to be added at the end of the simulation when `max_depth` is reached. This function will be called with two arguments, a `POMDP`, and a `ScenarioBelief`. It will not be called when the states in the belief are terminal.
