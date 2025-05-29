```
TabularVPolicy(V::Dict, domain, spec, default)
TabularVPolicy(domain, spec, default = NullPolicy())
```

Policy solution where state values are stored in a lookup table `V` that maps state hashes to values. The domain and specification also have to be provided, so that the policy knows how to derive action Q-values in each state.

A `default` policy can be specified, so that if a state doesn't already exist in the lookup table, the value returned by `default` will be used instead.
