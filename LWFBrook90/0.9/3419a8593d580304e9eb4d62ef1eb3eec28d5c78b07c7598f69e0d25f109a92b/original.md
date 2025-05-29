```
prepare_for_LWFBrook90R(s::DiscretizedSPAC; return_value = "inputs", out_dir = ".", file_suffix = "")
```

Transforms a SPAC model to input for the R package LWFBrook90R. Its return value depends on the argument return*value ∈ ["results", "inputs", "csv*paths"] The options are:

  * "results":    run LWFBrook90R and return the simulation results in Julia without writing to disk
  * "inputs":     return the input as DataFrames in Julia without writing to disk
  * "csv_paths":  write the input as .csv files to disk and return the paths ()

the current working directory for running with R.

Note that if `return_value = "results"` a working installation of R and LWFBrook90R v0.5.3 is required.
