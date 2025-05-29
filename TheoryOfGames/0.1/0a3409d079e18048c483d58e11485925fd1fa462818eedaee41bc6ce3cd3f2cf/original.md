```
in_core(mode, optimizer; verbose, ...)
```

Function to calculte a stable profit distribution that belongs to the core for profit distribution for a game described by the utility function and the grand coalition of player_set.

## Inputs

mode : IterMode     Calculation mode: enumerative technique optimizer : Any     Optimizer function for the JuMP model used for computation purposes verbose : Bool (optional, default true)     When true, it shows a progress bar to describe the current execution status

## Outputs

in*core*dist : Dict     Dictionary of the fair distributions of the profits among the players
