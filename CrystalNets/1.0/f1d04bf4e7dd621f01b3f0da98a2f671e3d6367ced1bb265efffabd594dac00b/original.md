```
determine_topology_dataset(path, save, autoclean, showprogress, options::Options)
determine_topology_dataset(path; save=true, autoclean=true, showprogress=true, kwargs...)
```

Given a path to a directory containing structure input files, compute the topology of each structure within the directory. Return a dictionary linking each file name to the result. The result is a [`InterpenetratedTopologyResult`](@ref), containing the topological genome, the name if known and the stability of the net. In case of error, the exception is reported.

Warnings will be toggled off (unless `force_warn` is set) and it is stongly recommended not to export any file since those actions may critically reduce performance, especially for numerous files.

If `save` is set, the result is also stored in a julia serialized file located at "$path/../results_$i" where `i` is the lowest integer such that this path does not already exist at the start of the computation. While processing, this path will be used to create a directory storing the current state of the computation: to continue an interrupted computation, simply pass this temporary directory as the path. If `autoclean` is set, this directory is removed at the end if the computation was successful.

If `save` is set and `autoclean` is unset, the directory of temporary files will be renamed into "$path/../results_$i.OLD$j".

If `showprogress` is set, a progress bar will be displayed representing the number of processed files.
