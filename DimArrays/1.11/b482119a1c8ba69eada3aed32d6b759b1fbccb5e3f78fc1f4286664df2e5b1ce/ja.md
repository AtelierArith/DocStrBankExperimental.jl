```
DimArray(T) = DimVector(T[])
DimArray(sym) = DimVector(Any[], sym)
```

後で `push!` できる空の `DimVector` で、オプションで次元名を指定できます。
