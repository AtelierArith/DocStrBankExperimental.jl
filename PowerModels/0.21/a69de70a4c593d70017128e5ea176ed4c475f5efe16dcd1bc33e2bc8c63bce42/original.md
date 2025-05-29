```
export_pti(io::IO, data::Dict{String, Any})
```

Export PowerModels network data dictionary to the as a power flow raw data acording to the pti format `RAW V33`. 

It is highly recommend to export the PowerModel data dictionary in the same format as the source data. 

The `export_pti` function exports the essential components of a network:

  * Buses
  * Loads
  * Fixed Shunts
  * Generators
  * Non Tansformers Branchs
  * Transformers (Two-Windings and Three-Windings)
  * Switched Shunts (aproximate)

If the PowerModels was parsed from a pti file with the `import_all=true` parameter: `data = parse_file(case3.raw, import_all=true)` 

It will export these aditionals items:

  * Header Options
  * Comment Lines
  * Zone Data
  * Area Data
  * Owner Data
  * Switched Shunts (with block steps)

Things that are not exported:

  * TNEP network specification
  * Generation Cost Data
  * Storage
  * Switches
  * DC Lines (future work, #754)

Things that are not exported if you use `import_all = true` to make the PowerModel data dict:

  * FACTS (Maybe in future work)
  * GNE (No intentions to export it)
  * Inter Area Transfer Data (No intentions to export it)
