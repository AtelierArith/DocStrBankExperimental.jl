```
MinActionCosts(terms, costs)
MinActionCosts(terms, actions, costs)
```

[`Goal`](@ref) specification where each action has a specific cost, and the goal formula is a conjunction of `terms`. Planners called with this specification will try to minimize the total action cost in the returned [`Solution`](@ref).

Costs can be provided as mapping from action names (specified as `Symbol`s) to `Real`s, such that each lifted action has an associated cost. Alternatively, costs can be provided as a mapping from ground action `Term`s to `Real`s. A mapping can be provided directly as a `NamedTuple` or `Dictionary`, or as a list of `actions` and corresponding `costs`.
