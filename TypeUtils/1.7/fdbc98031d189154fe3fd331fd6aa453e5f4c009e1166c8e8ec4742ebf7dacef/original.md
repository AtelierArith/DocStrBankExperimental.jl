```
convert_bare_type(T, x)
```

converts `x` so that its bare numeric type is that of `T`. Argument `x` may be a number or a numeric type, while argument `T` must be a numeric type. If `x` is one of `missing`, `nothing`, `undef`, or the type of one of these singletons, `x` is returned.

This method may be extended with `T<:TypeUtils.BareNumber` and for `x` of non-standard numeric type.
