```
fixed(val)
```

Represents a parameter whose value is required to stay constant. The `value` of a `Fixed` is simply `val`. Constantness of the parameter is enforced by returning an empty vector from `flatten`.
