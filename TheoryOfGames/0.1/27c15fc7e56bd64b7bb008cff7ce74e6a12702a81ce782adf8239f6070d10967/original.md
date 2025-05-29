```
utility_combs(player_set, utility)
```

Function to calculate the utility for every combination of players. This table may be used in Game Theory, such as in the calculation of the shapley value. The function iterates all combinations of players in the player_set and execute the utility function to identify the benefits to be shared.

## Inputs

player_set : Vector     Vector of the players utility : Function     Utility function that given any coalition returns the benefit of the coalition     It shall be a function utility(::Vector)::T<:Number verbose : Bool     When true, it shows a progress bar to describe the current execution status parallel : Bool     When true, paralleling is used to compute operations

## Outputs

utilities : Dict     Dictionary that specifies the utility of each combination of coalition in player_set
