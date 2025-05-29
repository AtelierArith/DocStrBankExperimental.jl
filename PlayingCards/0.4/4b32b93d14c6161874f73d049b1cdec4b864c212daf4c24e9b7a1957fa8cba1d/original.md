```
high_value(::Card)
high_value(::Rank)
```

The high rank value. For example:

  * `Rank(1)` -> 14 (use [`low_value`](@ref) for the low Ace value.)
  * `Rank(5)` -> 5
