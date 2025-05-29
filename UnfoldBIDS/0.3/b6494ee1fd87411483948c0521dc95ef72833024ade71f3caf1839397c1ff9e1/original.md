```
run_unfold(dataDF, bfDict; 
	eventcolumn="event",
	remove_time_expanded_Xs=true, 
	extract_data = raw_to_data, 
	verbose::Bool=true, 
	kwargs...)
```

Run Unfold analysis on all data in dataDF.

## Keywords

  * `eventcolumn::String = "event"`
     Which collumn Unfold should use during the analysis.
  * `remove_time_expanded_Xs::Bool = true`
     Removes the timeexpanded designmatrix which significantly reduces the memory-consumption. This Xs is rarely needed, but can be recovered (look into the Unfold.load function)
  * `extract_data::function = raw_to_data`
     Specify the function that translate the MNE Raw object to an data array. Default is `raw_to_data` which uses `get_data` and allows to pick `channels` - see @Ref(`raw_to_data`). The optional kw- arguments (e.g. channels) need to be specified directly in the `run_unfold` function as kw-args
  * `verbose::Bool = true)`
     Show ProgressBar or not.
