```
bridge_constraints(model::Model)
```

When in direct mode, return `false`. When in manual or automatic mode, return a `Bool` indicating whether the optimizer is set and unsupported constraints are automatically bridged to equivalent supported constraints when an appropriate transformation is available.
