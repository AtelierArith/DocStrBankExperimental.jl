```
load_bids_eeg_data(layout_df; verbose::Bool=true, kwargs...)
```

Load data found with [`bids_layout`](@ref) into memory.

  * `verbose::Bool = true`
     Show ProgressBar
  * `kwargs...`
     kwargs for CSV.read to load events from .tsv file; e.g. to specify delimeter
