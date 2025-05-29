```
NeXLUncertainties.asa(::Type{LaTeXString}, mat::Material; parsename=true, order = :massfraction | :z)
```

Converts a `Material` into a `LaTeXString`.  `parsename` controls whether the material name is assumed to be a parsable chemical formula (according to \ce{...}).
