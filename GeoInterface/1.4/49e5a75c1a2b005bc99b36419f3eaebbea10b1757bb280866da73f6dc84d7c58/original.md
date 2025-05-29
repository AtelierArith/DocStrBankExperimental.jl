```
GeoInterface.isgeometry(x) => Bool
```

Check if an object `x` is a geometry and thus implicitly supports GeoInterface methods. It is recommended that for users implementing `MyType`, they define only `isgeometry(::Type{MyType})`. `isgeometry(::MyType)` will then automatically delegate to this method.
