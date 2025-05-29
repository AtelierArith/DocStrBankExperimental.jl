```
G4JLDetectorGDML(gdmlfile::String; check_overlap::Bool, validate_schema::Bool, init_method::Union{Function,Nothing})
```

Initialize a G4JLDetector from a GDML file. The GDML file is parsed at this moment.

# Arguments

  * `gdmlfile::String`: GDML file name
  * `check_overlap::Bool=false`: check for overlaps
  * `validate_schema::Bool=true`: validate the schema
  * `init_method::Union{Function,Nothing}=nothing`: initialization method to be called when the detector is constructed
