```
least_core(mode, utilities, optimizer; verbose, raw_outputs)
```

Function to calculte the least core profit distribution for a game described by the utility function and the grand coalition of player_set.

## Inputs

mode : EnumMode     Calculation mode: enumerative technique player*set : Vector     Vector of the players of the coalition optimizer : Any     Optimizer function for the JuMP model used for computation purposes verbose : Bool (optional, default true)     When true, it shows a progress bar to describe the current execution status raw*outputs : Bool (optional, default false)     When true, it returns all raw outputs

## Outputs

leastcore_dist : Dict     Dictionary of the fair distributions of the profits among the players
