```
CertainValue
```

A simple wrapper type for values with no uncertainty (i.e. represented by a scalar).

## Examples

The two following ways of constructing values without uncertainty are equivalent. 

```julia
u1, u2 = CertainValue(2.2), CertainValue(6)
w1, w2 = UncertainValue(2.2), UncertainValue(6)
```
