```
ExtraActionCosts(spec::Specification, costs)
ExtraActionCosts(spec::Specification, actions, costs)
```

Wrapper that adds action-specific costs to an underlying `spec`.

Costs can be provided as mapping from action names (specified as `Symbol`s) to `Real`s, such that each lifted action has an associated cost. Alternatively, costs can be provided as a mapping from ground action `Term`s to `Real`s. A mapping can be provided directly as a `NamedTuple` or `Dictionary`, or as a list of `actions` and corresponding `costs`.
