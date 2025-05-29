```
wipe!(self::F) where {F<:AbstractField}
```

Wipe all the data from the field.

This includes values, prescribed values, degree of freedom numbers, and "is fixed" flags. The number of free degrees of freedom is set to zero.
