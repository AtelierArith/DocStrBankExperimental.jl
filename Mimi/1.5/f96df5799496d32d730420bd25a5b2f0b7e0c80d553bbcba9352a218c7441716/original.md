```
_save_trial_results(trial_df::DataFrame, datum_name::String, output_dir::String, 
                    streams::Dict{String, CSVFiles.CSVFileSaveStream{IOStream}})
```

Save the stored simulation results in `trial_df` from trial `trialnum` to files  in the directory `output_dir`
