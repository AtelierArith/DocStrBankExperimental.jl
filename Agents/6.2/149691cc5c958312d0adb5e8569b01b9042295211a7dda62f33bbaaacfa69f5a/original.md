```
positions(model::ABM{<:DiscreteSpace}) → ns
```

Return an iterator over all positions of a model with a discrete space.

```
positions(model::ABM{<:DiscreteSpace}, by::Symbol) → ns
```

Return all positions of a model with a discrete space, sorting them using the argument `by` which can be:

  * `:random` - randomly sorted
  * `:population` - positions are sorted depending on how many agents they accommodate. The more populated positions are first.
