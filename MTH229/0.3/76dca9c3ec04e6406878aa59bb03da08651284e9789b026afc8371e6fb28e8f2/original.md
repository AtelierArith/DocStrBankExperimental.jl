```
fubini(f, [zs], [ys], xs; rtol=missing, kws...)
```

Integrate `f` of 1, 2, or 3 input variables.

The zs may depend (x,y), the ys may depend on x

## Examples

```
# integrate over the unit square
fubini((x,y) -> sin(x-y), (0,1), (0,1))

# integrate over a triangle
fubini((x,y) -> 1, (0,identity), (0,1 ))

#
f(x,y,z) = x*y^2*z^3
fubini(f, (0,(x,y) ->  x+ y), (0, x -> x), (0,1))
```

!!! Note     This uses nested calls to `quadgk`. The use of `hcubature` is recommended, typically after a change of variables to make a rectangular domain. The relative tolerance increases at each nested level.
