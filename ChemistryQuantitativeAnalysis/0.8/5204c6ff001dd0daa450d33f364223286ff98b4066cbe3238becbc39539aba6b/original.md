```
AnalyteDataTable{A, S, N <: Real, T} <: AbstractDataTable{A, S, N, T}
```

Tabular data wrapper indicates part of columns represent analyte, and all rows reprsent samples. `A` determines analyte type, `S` determines sample type, `N` determines numeric value type, and `T` determines table type.

# Fields

  * `analyte`: `Vector{A}`, analytes in user-defined types, i.e., `getproperty(table(dt), analytecol(dt))`. Use `analyteobj` to get this field.
  * `sample`: `Vector{S}`, samples in user-defined types. Use `sampleobj` to get this field.
  * `analytecol`: `Symbol`, the column name that each element is analyte name. Use `analytecol` to get this field.
  * `table`: Tabular data of type `T`. Use `table` to get this field.

# Properties

All properties of `table`.
