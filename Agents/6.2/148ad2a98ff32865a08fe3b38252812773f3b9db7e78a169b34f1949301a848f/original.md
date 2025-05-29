```
iter_agent_groups(order::Int, model::ABM; scheduler = Schedulers.by_id)
```

Return an iterator over all agents of the model, grouped by order. When `order = 2`, the iterator returns agent pairs, e.g `(agent1, agent2)` and when `order = 3`: agent triples, e.g. `(agent1, agent7, agent8)`. `order` must be larger than `1` but has no upper bound.

Index order is provided by the `scheduler` input which is a scheduler.
