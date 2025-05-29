```
parentproperties(plan::RecoPlan)
```

Return a vector of property names of `plan` in its parent, s.t. `getproperty(parent(plan), last(parentproperties(plan))) === plan`. Return an empty vector if `plan` has no parent.
