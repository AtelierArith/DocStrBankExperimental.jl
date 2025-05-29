```
MinPerAgentActionCosts(terms, costs, [agent_arg_idx=1])
```

[`Goal`](@ref) specification where each agent has separate action costs. Planners called with this specification will try to minimize the total action cost in the returned [`Solution`](@ref).

Costs can be provided as a nested dictionary or named tuple, where the first level maps agent names (specified as `Symbol`s or `Const`s) to the second level, which maps action names or ground action `Term`s to `Real`s.

The `agent_arg_idx` argument specifies the index of the agent argument in the action terms. By default, this is 1.
