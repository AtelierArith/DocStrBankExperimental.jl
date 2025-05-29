```
proc_n_save(procwhole_fn, procsubset_fn, postproc_fn;
    xlfile,
    datafiles=nothing, 
    paramsets = [(;)],
    ) → (; overview, subsets_results, résumé, errors, dfs)
```

Calls [`proc_data`](@ref) with the user provided functions to process data followed by [`save_results`](@ref).  For explanation of arguments and returned values see docs on these functions.

Function `proc_n_save` is exported.
