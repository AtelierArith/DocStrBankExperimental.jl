```
whichmodule(::Type{T}) where T
```

Return the module in which `T` was CBOO-ified.

NOTE: this uses information stored by CBOOCall. Might be the same as info retrievable through Julia.
