```
value_or_shadow_price(constraints, obj_scalar) -> shadow_prices*obj_scalar

value_or_shadow_price(variables, obj_scalar) -> values

value_or_shadow_price(expressions, obj_scalar) -> values
```

Returns a value or shadow price depending on what is passed in.  Used in [`results_raw!`](@ref).  Scales shadow prices by `obj_scalar` to restore to units of dollars (per applicable unit).
