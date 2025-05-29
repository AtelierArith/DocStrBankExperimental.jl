```
objective(i::CombinatorialInstance)
```

Returns the objective associated with this instance. 

By default, instances are supposed to provide an `objective` member, but this function can be overridden otherwise (for instance, when only one objective is supported).
