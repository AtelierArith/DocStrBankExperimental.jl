A helper functions to return the base value from a variable to use when creating other variables. It is especially useful for taking two model arguments and creating a new variable compatible with both arguments.

```julia
compatible_values(x,y)
compatible_values(x)
```

It's still somewhat broken but works for basic cases. No type promotion is currently done.

### Arguments

  * `x`, `y` : objects or variables

### Returns

The returned object has zeros of type and length common to both `x` and `y`.

### Examples

```julia
a = Unknown(45.0 + 10im)
x = Unknown(compatible_values(a))   # Initialized to 0.0 + 0.0im.
a = Unknown()
b = Unknown([1., 0.])
y = Unknown(compatible_values(a,b)) # Initialized to [0.0, 0.0].
```
