```
whichmodule(::Type{T}) where T
```

Return the module in which `T` was DotCall-ified.

NOTE: this uses information stored by DotCall. Might be the same as info retrievable through Julia.
