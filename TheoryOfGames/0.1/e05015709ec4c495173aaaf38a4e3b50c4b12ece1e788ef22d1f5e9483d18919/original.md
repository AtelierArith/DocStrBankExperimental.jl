```
specific_in_core(mode, dist_objective, optimizer; verbose, raw_outputs)
```

Function to calculte a stable profit distribution that belongs to the core and maximizes a specific distribution objective specified by dist*objective for a game described by the utility function and the grand coalition of player*set.

## Inputs

mode : EnumMode     Calculation mode: enumerative technique dist*objective : Function     Function to build the objective function of the profit distribution     It shall a function with two arguments, which are the JuMP model and the player set,     and it shall build the objective functions using the JuMP @NLobjective or @objective     commands optimizer : Any     Optimizer function for the JuMP model used for computation purposes verbose : Bool (optional, default true)     When true, it shows a progress bar to describe the current execution status raw*outputs : Bool (optional, default false)     When true, it returns all raw outputs

## Outputs

specific*in*core_dist : Dict     Dictionary of the fair distributions of the profits among the players
