```
remove!(unitCatalogue::UnitCatalogue, name::String)
```

Remove the [`UnitFactorElement`](@ref) object of name `name` from `unitCatalogue`.

# Raises Exception

  * `Base.KeyError`: if attempting to delete a non-existent element
