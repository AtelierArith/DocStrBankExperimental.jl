```
DimArray(T) = DimVector(T[])
DimArray(sym) = DimVector(Any[], sym)
```

Empty `DimVector` into to which you can later `push!` things, optionally with a dimension name.
