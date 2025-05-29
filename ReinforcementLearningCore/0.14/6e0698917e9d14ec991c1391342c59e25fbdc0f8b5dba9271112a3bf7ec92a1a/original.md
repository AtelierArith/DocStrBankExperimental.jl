```
prob(s::EpsilonGreedyExplorer, values) ->Categorical
prob(s::EpsilonGreedyExplorer, values, mask) ->Categorical
```

Return the probability of selecting each action given the estimated `values` of each action.
