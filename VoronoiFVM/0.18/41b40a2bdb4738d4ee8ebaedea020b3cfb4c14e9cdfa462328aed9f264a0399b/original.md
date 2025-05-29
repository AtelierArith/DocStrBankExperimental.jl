```
TransientSolution(t0,inival;
                  in_memory=true,
                  keep_open=true,
                  fname=tempname(pwd())*".jld2"
```

Constructor of transient solution with initial value and inital time.

  * `in_memory`: if true (default), data are kept in main memory, otherwise on disk (via JLD2)
  * `keep_open`: if true, disk file is not closed during the existence of the object
  * `fname`: file name for the disk file
