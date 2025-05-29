```
getbounds(sys::ModelingToolkit.AbstractSystem, p = parameters(sys))
```

Returns a dict with pairs `p => (lb, ub)` mapping parameters of `sys` to lower and upper bounds. Create parameters with bounds like this

```
@parameters p [bounds=(-1, 1)]
```

To obtain state bounds, call `getbounds(sys, states(sys))`
