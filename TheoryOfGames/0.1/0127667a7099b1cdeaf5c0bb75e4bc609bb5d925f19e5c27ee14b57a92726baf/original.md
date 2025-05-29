```
shapley_value(mode; verbose)
```

Function to calculte the shapley value for a game described by the utility function and the grand coalition of player_set.

## Inputs

mode : EnumMode     Calculation mode: enumerative technique verbose : Bool (optional, default true)     When true, it shows a progress bar to describe the current execution status

## Outputs

shapley_value : Dict     Dictionary of the fair distributions of the profits among the players
