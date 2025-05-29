```
 ValueDictPolicy(mdp)
```

A generic MDP policy that consists of a `Dict` storing Q-values for state-action pairs. If there are no entries higher than a default value, this will fall back to a default policy.

# Keyword Arguments

  * `value_table::AbstractDict` the value dict, key is (s, a) Tuple.
  * `default_value::Float64` the defalut value of `value_dict`.
  * `default_policy::Policy` the policy taken when no action has a value higher than `default_value`
