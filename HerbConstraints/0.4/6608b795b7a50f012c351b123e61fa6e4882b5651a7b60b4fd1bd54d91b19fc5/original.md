```
StateHole <: AbstractUniformHole
```

`StateHole`s are uniform holes used by the `UniformSolver`. Domain manipulations are tracked for backpropagation.

  * `domain`: A `StateSparseSet` representing the rule nodes this hole can take. If size(domain) == 1, this hole should act like a `RuleNode`
  * `children`: The children of this hole in the expression tree.
