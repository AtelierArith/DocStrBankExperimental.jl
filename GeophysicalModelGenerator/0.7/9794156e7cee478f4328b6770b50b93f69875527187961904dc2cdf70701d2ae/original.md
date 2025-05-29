```
create_partitioning_file(LaMEM_input::String, NumProc::Int64; LaMEM_dir::String=pwd(), LaMEM_options::String="", MPI_dir="", verbose=true)
```

This executes LaMEM for the input file `LaMEM_input` & creates a parallel partitioning file for `NumProc` processors. The directory where the LaMEM binary is can be specified; if not it is assumed to be in the current directory. Likewise for the `mpiexec` directory (if not specified it is assumed to be available on the command line).
