```
TabularModel([::Type,] num_states; num_outputs, num_actions)
```

Creates a tabular model that is a special case of the tile coding model that uses an identity basis function, with one tiling, and number of tiles equal to the number of states. This means for state input `s`, `m(s)` will prediction in that state or list of predictions for each action if `num_actions` > 1. Similarly, `m(s,a)` will predict the value of action `a` in state `s`. TabularModel also inherits all the functionality of the TileCodingModel, e.g., `params`, `value_withgrad`, etc.

See also: [`TileCodingModel`](@ref), [`LinearModel`](@ref)
