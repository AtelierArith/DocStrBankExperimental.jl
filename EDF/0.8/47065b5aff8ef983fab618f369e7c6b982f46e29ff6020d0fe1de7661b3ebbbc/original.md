```
EDF.PatientID
```

A type representing the local patient identification field of an EDF+ header.

See EDF+ specification for details.

# Fields

  * `code::Union{String,Missing}`
  * `sex::Union{Char,Missing}` (`'M'`, `'F'`, or `missing`)
  * `birthdate::Union{Date,Missing}`
  * `name::Union{String,Missing}`
