```
parse_file(
    path::String;
    skip_correct::Bool=false,
    per_unit::Bool=true
)
```

Parses an [EPANET](https://www.epa.gov/water-research/epanet) (.inp) or JavaScript Object Notation (JSON) file from the file path `path`, depending on the file extension, and returns a WaterModels data structure (i.e., a dictionary of data). Here, `skip_correct` will skip data correction routines (e.g., component status propagation) if set to `true`, and `per_unit` will translate the data model to a per-unit measurement system if set to `true`.
