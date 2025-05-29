```
floating_point_type(args...) -> T <: AbstractFloat
```

yields an appropriate floating-point type to represent the promoted numeric type used by arguments `args...` for storing their value(s). Any units of the arguments are ignored and the returned type is always unitless.

For numerical computations, a typical usage is:

```
T = floating_point_type(x, y, ...)
xp = convert_real_type(T, x)
yp = convert_real_type(T, y)
...
```

to have numbers `x`, `y`, etc. converted to an appropriate common floating-point type while preserving their units if any.

Also see [`real_type`](@ref) and [`convert_real_type`](@ref).

---

```
floating_point_type() -> AbstractFloat
```

yields the supertype of the types that may be returned by `floating_point_type` when called with no arguments.
