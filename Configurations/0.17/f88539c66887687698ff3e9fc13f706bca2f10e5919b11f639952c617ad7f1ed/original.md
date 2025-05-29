```
from_kwargs(convention!, ::Type{T}; kw...) where T
```

Convert keyword arguments to given option type `T` using `convention!`. See also [`from_dict`](@ref).

# Convention

  * `from_underscore_kwargs!`: use `_` to disambiguate subfields of the same name, this is the default behaviour.
  * `from_field_kwargs!`: do not disambiguate subfields, errors if there are disambiguity
