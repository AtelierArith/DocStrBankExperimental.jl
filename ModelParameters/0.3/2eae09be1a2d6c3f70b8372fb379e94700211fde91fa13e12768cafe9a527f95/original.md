```
Param(p::NamedTuple)
Param(; kw...)
Param(val)
```

A wrapper type that lets you extract model parameters and metadata about the model like bounding val, units priors, or anything else you want to attach.

The first argument is assigned to the `val` field, and if only keyword arguments are used, `val`, must be one of them. `val` is used as the number val if the model us run without stripping out the `Param` fields. `stripparams` also takes only the `:val` field.
