```
from_dict(::Type{OptionType}, ::Type{T}, x) where {OptionType, T}
```

For option type `OptionType`, convert the object `x` to type `T`. This is similar to `Base.convert(::Type{T}, x)` and will fallback to `Base.convert` if not defined.
