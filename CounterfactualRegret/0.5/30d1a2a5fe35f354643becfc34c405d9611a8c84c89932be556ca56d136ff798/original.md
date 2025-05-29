```
OSCFRSolver(game; method=Vanilla(), baseline=ZeroBaseline(), ϵ::Float64 = 0.6)
```

Instantiate outcome sampling CFR solver with some `game`.

Samples a single actions from all players for single tree traversal. Time to complete a traversal is O(d), where d is the depth of the game.

`ϵ` - exploration parameter

Available baselines:

  * [`ZeroBaseline`](@ref) - Equivalent to no baseline
  * [`ExpectedValueBaseline`](@ref)
