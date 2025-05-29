```
read_b2time_output(filename::String)::Dict{String, Dict{String, Any}}
```

Read time dependent b2 output file and return a dictionary with structure: Dict("dim" => Dict{String, Any}, "data" => Dict{String, Any}) where "dim" contains the dimensions of the data and "data" contains the data itself, with keys corresponding to the field names.

Supported SOLPS files as input via filename:

  * b2time.nc
