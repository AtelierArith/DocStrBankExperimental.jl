```
add!(unitCatalogue::UnitCatalogue, unitPrefix::UnitPrefix)
add!(unitCatalogue::UnitCatalogue, baseUnit::BaseUnit)
```

Add a [`UnitFactorElement`](@ref) to `unitCatalogue`.

No element with the same name as the element to add may already exist in `unitCatalogue`.

# Raises Exception

  * `Alicorn.Exceptions.DuplicationError`: if a [`UnitFactorElement`](@ref) carrying the same `name` field as the element to add already exists in `unitCatalogue`.
