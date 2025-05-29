```
ObjectScheme

ObjectScheme()
```

Default colorscheme. Similar to `GreyScale` for `Number`.

Other grid objects can define a custom method to return colors from composite objects:

```julia
DynamicGrids.to_rgb(::ObjectScheme, obj::MyObjectType) = ...
```

Which must return an `ARGB32` value.
