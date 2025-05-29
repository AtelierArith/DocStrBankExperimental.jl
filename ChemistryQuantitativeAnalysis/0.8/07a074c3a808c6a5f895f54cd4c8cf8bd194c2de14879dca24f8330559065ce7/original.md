```
AnalysisTable{A, S, T <: AbstractDataTable{A, S}}
```

Wrapper of multiple tables representing different types of values. `A` determines analyte type, `S` determines sample type, and `T` determines datatable type. It is implemented as a `Dictionary{Symbol, T <: AbstractDataTable{A, S}}`, but unlike dictionaries, each datatable can also be extracted using `getproperty`. 

# Fields

  * `analyte`: `Vector{A}`, analytes in user-defined types. Use `analyteobj` to get this field.
  * `sample`: `Vector{S}`, samples in user-defined types. Use `sampleobj` to get this field.
  * `tables`: `Dictionary{Symbol, T}`, a dictionary mapping data type to datatable. Use `tables` to get this field.

# Properties

All keys of `tables`.
