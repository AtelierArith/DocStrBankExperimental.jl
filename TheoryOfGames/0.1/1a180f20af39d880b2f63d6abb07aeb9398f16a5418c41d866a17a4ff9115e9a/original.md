```
verify_in_core(profit_dist, mode, optimizer; verbose, utilities)
```

Function to calculte whether a given profit distribution belongs to the core. The game shall be described by the utility function and the grand coalition of player_set.

## Inputs

mode : EnumMode     Calculation mode: enumerative technique optimizer : Any     Optimizer function for the JuMP model used for computation purposes verbose : Bool (optional, default true)     When true, it shows a progress bar to describe the current execution status

## Outputs

in*core*dist : Dict     Dictionary of the fair distributions of the profits among the players
