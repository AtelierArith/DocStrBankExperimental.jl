```
save_results(results::DataFrame, bids_root::String; 
    derivatives_subfolder::String="Unfold",
    overwrite::Bool=false)
```

Function to save unfold models in your BIDS root folder. Automatically creates a `derivatives_subfolder` (default = "Unfold") in the derivatives and subsequentely safes each model in results according to BIDS. Example of path to saved file: `bids_root/derivatives/Unfold/sub-XXX/eeg/sub-XXX_ses-XX_task-XXX_run-XX_unfold.jld2`

# Keywords

  * `derivatives_subfolder::String = "Unfold"`
     Creates the named subfolder and saves Unfold models according to BIDS.
  * `overwrite::Bool = false`
     Does not overwrite existing datasets; can be set to true.
