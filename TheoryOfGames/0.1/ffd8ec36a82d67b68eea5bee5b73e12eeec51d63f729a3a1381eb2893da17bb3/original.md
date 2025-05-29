```
var_least_core(mode, optimizer; verbose)
```

Function to calculte a stable profit distribution that belongs to the least core and minimizes the variance of the profit allocation among the players for a game described by the utility function and the grand coalition of player_set.

## Inputs

mode : EnumMode     Calculation mode: enumerative technique optimizer : Any     Optimizer function for the JuMP model used for computation purposes verbose : Bool (optional, default true)     When true, it shows a progress bar to describe the current execution status

## Outputs

specific*least*core_dist : Dict     Dictionary of the fair distributions of the profits among the players
