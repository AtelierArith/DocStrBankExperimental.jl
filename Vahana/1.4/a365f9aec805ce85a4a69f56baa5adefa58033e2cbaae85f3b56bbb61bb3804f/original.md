```
create_simulation(model::Model, [params = nothing, globals = nothing; name = model.name, filename = name, overwrite_file = true, logging = false, debug = false])
```

Creates and return a new simulation object, which stores the complete state  of a simulation. 

`model` is an `Model` instance created by [`create_model`](@ref).

`params` must be a struct (or `nothing`) that contains all parameters of a simulation. Parameter values are constant in a simulation run and can be retrieved via the [`param`](@ref) function.

`globals` must be a mutable struct (or `nothing`). The values of these fields are accessible for all agents via the [`get_global`](@ref) function. The values can be changed by calling [`set_global!`](@ref) or [`push_global!`](@ref). 

The optional keyword argument `name` is used as meta-information about the simulation and has no effect on the dynamics, since `name` is not accessible in the transition functions. If `name` is not given, the name of the model is used instead.

The optional `filename` keyword is a string that will be used as the name of the hdf5 file when a simulation or a part of it is written via e.g. [`write_snapshot`](@ref). 

The file is created when a `write...` function is called for the first time, and it is created in an `h5` subfolder. By default an existing file with the same `filename` will be overwritten, but this behavior can be disabled with the `overwrite_file` keyword, in which case the files will be numbered. If `filename` is not provided, the `name` argument is used instead.

The keywords `logging` is a boolean flag that enables an automatical log file.  The log file contains information such as the time spent in different functions. When also `debug` is set to true, the log file contains more details and the stream will be flushed after each write.

As with the hdf5 files, overwrite_file `the` keyword determines whether the log files are overwritten or numbered. The numbering is set independently from the numbering of the hdf5 files.

The simulation starts in an uninitialized state. After adding the agents and edges for the initial state, it is necessary to call [`finish_init!`](@ref) before applying a transition function for the first time.

See also [`create_model`](@ref), [`param`](@ref), [`get_global`](@ref), [`set_global!`](@ref), [`push_global!`](@ref) and [`finish_init!`](@ref)
