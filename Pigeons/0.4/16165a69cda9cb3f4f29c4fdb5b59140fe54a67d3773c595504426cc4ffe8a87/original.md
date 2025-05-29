```julia
PT(source_exec_folder; round, exec_folder)

```

Create a [`PT`](@ref) struct from a saved  checkpoint. The input `source_exec_folder` should point to a folder of the form  `results/all/[exec_folder]`.

The checkpoint carries all the information stored in  a [`PT`](@ref) struct. It is possible for an MPI-based  execution to load a checkpoint written by a single-process  execution and vice versa.

A new unique folder will be created with symlinks to  the source one, so that e.g. running more rounds of  PT will results in a new space-efficient checkpoint  containing all the information for the new run.
