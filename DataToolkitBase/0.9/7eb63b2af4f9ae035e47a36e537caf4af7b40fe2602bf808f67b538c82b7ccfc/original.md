```
typeify(qt::QualifiedType; mod::Module=Main)
```

Convert `qt` to a `Type` available in `mod`, if possible. If this cannot be done, `nothing` is returned instead.
