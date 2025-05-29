```
ConstrainedResetMap
```

A reset map with state constraints of the form

$$
    x ↦ R(x), x ∈ \mathcal{X},
$$

such that the specified variables are assigned a given value, and the remaining variables are unchanged.

### Fields

  * `dim`  – dimension
  * `X`    – state constraints
  * `dict` – dictionary whose keys are the indices of the variables that are           reset, and whose values are the new values
