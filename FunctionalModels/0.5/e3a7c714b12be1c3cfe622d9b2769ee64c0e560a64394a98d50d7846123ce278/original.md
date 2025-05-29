A helper functions to return the base NaN value from a variable to use when creating other variables. It is especially useful for taking two model arguments and creating a new variable compatible with both arguments. This differs fron `compatible_values` in that it returns  values filled with NaNs to indicate a variable without a default value.

```julia
compatible_shape(x,y)
compatible_shape(x)
```

It's still somewhat broken but works for basic cases. No type promotion is currently done.

### Arguments

  * `x`, `y` : objects or variables

### Returns

The returned object has NaNs of type and length common to both `x` and `y`.

### Examples

```julia
a = Unknown(45.0 + 10im)
x = Unknown(compatible_shape(a))   # Initialized to NaN + NaNim.
a = Unknown()
b = Unknown([1., 0.])
y = Unknown(compatible_shape(a,b)) # Initialized to [NaN, NaN].
```
