```
parentproperty(plan::RecoPlan)
```

Return the property name of `plan` in its parent, s.t. `getproperty(parent(plan), parentproperty(plan)) === plan`. Return `nothing` if `plan` has no parent.
