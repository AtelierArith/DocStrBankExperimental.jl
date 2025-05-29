```julia
TamuSystem(tamu_folder::AbstractString; kwargs...) -> Any

```

Creates a system from a PSS/e .RAW (v33) load flow case, and an associated .csv with MW load time series data. The format is established by the [Texas A&M University Test Case Archive](https://electricgrids.engr.tamu.edu/electric-grid-test-cases/)

The general format for data is folder:    [casename].raw    [casename]*load*time*series*MW.csv

# Arguments

  * `directory::AbstractString`: directory containing RAW and CSV files

# Examples

```julia
sys = TamuSystem(
    "./ACTIVSg25k",
    config_path = "ACTIVSg25k_validation.json",
    bus_name_formatter = x->string(x["name"]*"-"*string(x["index"])),
    load_name_formatter = x->strip(join(x["source_id"], "_"))
)
```
