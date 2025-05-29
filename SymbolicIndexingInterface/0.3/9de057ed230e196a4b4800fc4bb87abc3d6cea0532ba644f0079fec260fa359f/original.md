```
parameter_values(valp)
parameter_values(valp, i)
```

Return an indexable collection containing the value of each parameter in `valp`. The two- argument version of this function returns the parameter value at index `i`. The two-argument version of this function will default to returning `parameter_values(valp)[i]`.

If this function is called with an `AbstractArray` or `Tuple`, it will return the same array/tuple.
