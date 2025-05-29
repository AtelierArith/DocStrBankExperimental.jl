```
G4JLMagneticField(name::String, data::DATA; <keyword arguments>) where DATA<:G4JLGeneratorData
```

Create a G4JLMagneticField with its name and associated DATA structure

# Arguments

  * `name::String`: magnetic field name
  * `data::DATA`: data structure associated to the magnetic field
  * `getfield_method=nothing`: user provided `getfield` function with signature: `(result::G4ThreeVector, position::G4ThreeVector, ::DATA)`
