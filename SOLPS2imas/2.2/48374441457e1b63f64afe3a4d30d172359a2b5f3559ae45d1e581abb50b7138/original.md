```
read_b2_output(filename::String)::Dict{String, Dict{String, Any}}
```

Read final state b2 output file (b2fstate or b2time.nc) or b2fgmtry file and return a dictionary with structure: Dict("dim" => Dict{String, Any}, "data" => Dict{String, Any}) where "dim" contains the dimensions of the data and "data" contains the data itself, with keys corresponding to the field names.

Supported SOLPS files as input via filename:

  * b2fstate
  * b2fstati
  * b2time.nc
  * b2fgmtry
