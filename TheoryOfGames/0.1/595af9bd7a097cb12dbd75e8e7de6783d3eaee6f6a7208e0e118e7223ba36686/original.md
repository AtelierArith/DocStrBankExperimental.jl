```
nucleolus(mode, utilities; verbose, tol, raw_outputs)
```

Function to calculte the nucleolus profit distribution for a game described by the utility function and the grand coalition of player_set.

## Inputs

mode : EnumMode     Calculation mode: enumerative technique optimizer : Any     Optimizer function for the JuMP model used for computation purposes verbose : Bool (optional, default true)     When true, it shows a progress bar to describe the current execution status tol (optional, default 1e-5)     Accepted tolerance for identifying the active constraints in the optimization     procedure raw_outputs : Bool (optional, default false)     When true, it returns all raw outputs

## Outputs

nucleolus_dist : Dict     Dictionary of the fair distributions of the profits among the players
