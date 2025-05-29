```
ExtraPerAgentActionCosts(spec::Specification, costs, [agent_arg_idx=1])
```

Wrapper that adds per-agent action costs to an underlying `spec`.

Costs can be provided as a nested dictionary or named tuple, where the first level maps agent names (specified as `Symbol`s or `Const`s) to the second level, which maps action names or ground action `Term`s to `Real`s.
