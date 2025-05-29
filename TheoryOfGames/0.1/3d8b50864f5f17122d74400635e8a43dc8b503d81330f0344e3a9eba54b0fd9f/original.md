```
specific_least_core(mode, dist_objective, optimizer; verbose, raw_outputs)
```

Function to calculte a stable profit distribution that belongs to the least core and minimizes a specific objective for the profit allocation among the plauers, for a game described by the utility function and the grand coalition of player_set.

## Inputs

mode : EnumMode     Calculation mode: enumerative technique dist*objective : Function     Function to build the objective function of the profit distribution, after the least core     is obtained     It shall be a function with two arguments: the JuMP model of the problem and the player set,     and the function shall build the desired objective functions using the      JuMP @NLobjective or @objective commands optimizer : Any     Optimizer function for the JuMP model used for computation purposes verbose : Bool (optional, default true)     When true, it shows a progress bar to describe the current execution status raw*outputs : Bool (optional, default false)     When true, it returns all raw outputs

## Outputs

specific*least*core_dist : Dict     Dictionary of the fair distributions of the profits among the players
