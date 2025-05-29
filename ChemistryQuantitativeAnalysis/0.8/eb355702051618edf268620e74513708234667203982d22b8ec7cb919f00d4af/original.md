```
SampleDataTable{A, S, N <: Real, T} <: AbstractDataTable{A, S, N, T}
```

Tabular data wrapper indicates part of columns represent analytes, and all rows reprsent samples. `A` determines analyte type, `S` determines sample type, `N` determines numeric value type, and `T` determines table type.

# Fields

  * `analyte`: `Vector{A}`, analytes in user-defined types. Use `analyteobj` to get this field.
  * `sample`: `Vector{S}`, samples in user-defined types, i.e., `getproperty(table(dt), samplecol(dt))`. Use `sampleobj` to get this field.
  * `samplecol`: `Symbol`, the column name that each element is sample name. Use `samplecol` to get this field.
  * `table`: Tabular data of type `T`. Use `table` to get this field.

# Properties

All properties of `table`.
