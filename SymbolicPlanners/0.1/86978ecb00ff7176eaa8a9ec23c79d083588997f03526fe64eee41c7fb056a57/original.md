```
TabularPolicy(V::Dict, Q::Dict, default)
TabularPolicy(default = NullPolicy())
```

Policy solution where state values and action Q-values are stored in lookup tables `V` and `Q`, where `V` maps state hashes to values, and `Q` maps state hashes to dictionaries of Q-values for each action in the corresponding state.

A `default` policy can be specified, so that if a state doesn't already exist in the lookup tables, the value returned by `default` will be used instead.
