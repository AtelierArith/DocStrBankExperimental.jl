```
from_dict(::Type{OptionType}, ::OptionField{f_name}, ::Type{T}, x) where {OptionType, f_name, T}
```

For option type `OptionType`, convert the object `x` to the field type `T` and assign it to the field `f_name`. Raise `FieldTypeConversionError`s errors if `Base.convert` raises exception

```
ERROR: MethodError: Cannot `convert` an object of type ...
```
