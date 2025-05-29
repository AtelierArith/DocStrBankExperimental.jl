```
ref_in_core(mode, ref_dist, optimizer; verbose)
```

Function to calculte a stable profit distribution that belongs to the core and minimizes the variance of the profit allocation among the players with respect to a pre-defined reward distribution function for a game described by the utility function and the grand coalition of player_set.

## Inputs

mode : IterMode     Calculation mode: enumerative technique ref*dist : AbstrctDict     Reference distribution by player optimizer : Any     Optimizer function for the JuMP model used for computation purposes norm : Any     Normalization denominator for every player     Default value nothing, hence for every player the Normalization     factor is 1.0 numerical*multiplier : Float (default 1e-3)     Multiplier to adjust numerical issues verbose : Bool (optional, default true)     When true, it shows a progress bar to describe the current execution status

## Outputs

specific*ref*in*core*dist : Dict     Dictionary of the fair distributions of the profits among the players
