```
StorePlan(sample_time,varlist[;htype=RegularHistory,min_time=-Inf,max_time=Inf])
```

Create a plan for storing history data. The storage of data is specied to occur at a sample interval given by `sample_time`. Optionally, one can also specify the initial time `min_time` and final time `max_time` (included) for a sampling window. These default to all times. The list of variables to be stored is specified as a list of variables `varlist`, provided as comma-separated named pairs, e.g. `"varname1"-> v1,"varname2"-> v2`. The optional argument `htype` can be used to set the history data to `PeriodicHistory` or `RegularHistory` (the default). In the case of `PeriodicHistory`, the data is assumed to repeat with a period equal to length(history)+1.
