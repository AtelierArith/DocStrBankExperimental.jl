```
value_or_shadow_price(constraints, obj_scalar) -> shadow_prices*obj_scalar

value_or_shadow_price(variables, obj_scalar) -> values

value_or_shadow_price(expressions, obj_scalar) -> values
```

渡されたものに応じて値またはシャドウプライスを返します。 [`results_raw!`](@ref) で使用されます。 シャドウプライスを `obj_scalar` でスケールして、ドルの単位（適用可能な単位あたり）に戻します。
