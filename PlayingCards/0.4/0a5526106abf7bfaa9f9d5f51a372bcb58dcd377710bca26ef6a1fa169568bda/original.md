```
low_value(::Card)
low_value(::Rank)
```

The low rank value. For example:

  * `Rank(1)` -> 1 (use [`high_value`](@ref) for the high Ace value.)
  * `Rank(5)` -> 5
