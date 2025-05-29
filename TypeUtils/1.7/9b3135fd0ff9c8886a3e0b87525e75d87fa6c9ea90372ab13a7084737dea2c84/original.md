```
convert_floating_point_type(T, x)
```

converts `x` so that its bare real type is the floating-point type of `T`. Argument `x` may be a number or a numeric type, while argument `T` must be a numeric type. If `x` is one of `missing`, `nothing`, `undef`, or the type of one of these singletons, `x` is returned.

This method may be extended with `T<:AbstractFloat` and for `x` of non-standard numeric type.
