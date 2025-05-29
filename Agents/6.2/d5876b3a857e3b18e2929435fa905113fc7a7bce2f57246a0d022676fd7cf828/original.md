```
nearby_ids(agent::AbstractAgent, model::ABM, r=1)
```

Same as `nearby_ids(agent.pos, model, r)` but the iterable *excludes* the given `agent`'s id.
