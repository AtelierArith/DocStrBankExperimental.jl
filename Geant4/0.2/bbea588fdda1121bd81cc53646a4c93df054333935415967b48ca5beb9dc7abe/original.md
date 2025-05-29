```
G4JLSensitiveDetector(name::String, data::DATA; <keyword arguments>) where DATA<:G4JLSDData
```

Initialize a G4JLSensitiveDetector with its name and associated DATA structure.

# Arguments

  * `name::String`: Sensitive detector name
  * `data::DATA`: Data structure associted to the sensitive detector
  * `processhits_method=nothing`: processHit function with signature: `(data::DATA, step::G4Step, ::G4TouchableHistory)::Bool`
  * `initialize_method=nothing`: intialize function with signature: `(data::DATA, ::G4HCofThisEvent)::Nothing`
  * `endofevent_method=nothing`: endOfEvent function with signature: `(data::DATA, ::G4HCofThisEvent)::Nothing`
