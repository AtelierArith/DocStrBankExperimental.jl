```
equation_search(X, y[; kws...])
```

Perform a distributed equation search for functions `f_i` which describe the mapping `f_i(X[:, j]) ≈ y[i, j]`. Options are configured using SymbolicRegression.Options(...), which should be passed as a keyword argument to options. One can turn off parallelism with `numprocs=0`, which is useful for debugging and profiling.

# Arguments

  * `X::AbstractMatrix{T}`:  The input dataset to predict `y` from.   The first dimension is features, the second dimension is rows.
  * `y::Union{AbstractMatrix{T}, AbstractVector{T}}`: The values to predict. The first dimension   is the output feature to predict with each equation, and the   second dimension is rows.
  * `niterations::Int=100`: The number of iterations to perform the search.   More iterations will improve the results.
  * `weights::Union{AbstractMatrix{T}, AbstractVector{T}, Nothing}=nothing`: Optionally   weight the loss for each `y` by this value (same shape as `y`).
  * `options::AbstractOptions=Options()`: The options for the search, such as   which operators to use, evolution hyperparameters, etc.
  * `variable_names::Union{Vector{String}, Nothing}=nothing`: The names   of each feature in `X`, which will be used during printing of equations.
  * `display_variable_names::Union{Vector{String}, Nothing}=variable_names`: Names   to use when printing expressions during the search, but not when saving   to an equation file.
  * `y_variable_names::Union{String,AbstractVector{String},Nothing}=nothing`: The   names of each output feature in `y`, which will be used during printing   of equations.
  * `parallelism=:multithreading`: What parallelism mode to use.   The options are `:multithreading`, `:multiprocessing`, and `:serial`.   By default, multithreading will be used. Multithreading uses less memory,   but multiprocessing can handle multi-node compute. If using `:multithreading`   mode, the number of threads available to julia are used. If using   `:multiprocessing`, `numprocs` processes will be created dynamically if   `procs` is unset. If you have already allocated processes, pass them   to the `procs` argument and they will be used.   You may also pass a string instead of a symbol, like `"multithreading"`.
  * `numprocs::Union{Int, Nothing}=nothing`:  The number of processes to use,   if you want `equation_search` to set this up automatically. By default   this will be `4`, but can be any number (you should pick a number <=   the number of cores available).
  * `procs::Union{Vector{Int}, Nothing}=nothing`: If you have set up   a distributed run manually with `procs = addprocs()` and `@everywhere`,   pass the `procs` to this keyword argument.
  * `addprocs_function::Union{Function, Nothing}=nothing`: If using multiprocessing   (`parallelism=:multiprocessing`), and are not passing `procs` manually,   then they will be allocated dynamically using `addprocs`. However,   you may also pass a custom function to use instead of `addprocs`.   This function should take a single positional argument,   which is the number of processes to use, as well as the `lazy` keyword argument.   For example, if set up on a slurm cluster, you could pass   `addprocs_function = addprocs_slurm`, which will set up slurm processes.
  * `heap_size_hint_in_bytes::Union{Int,Nothing}=nothing`: On Julia 1.9+, you may set the `--heap-size-hint`   flag on Julia processes, recommending garbage collection once a process   is close to the recommended size. This is important for long-running distributed   jobs where each process has an independent memory, and can help avoid   out-of-memory errors. By default, this is set to `Sys.free_memory() / numprocs`.
  * `worker_imports::Union{Vector{Symbol},Nothing}=nothing`: If you want to import   additional modules on each worker, pass them here as a vector of symbols.   By default some of the extensions will automatically be loaded when needed.
  * `runtests::Bool=true`: Whether to run (quick) tests before starting the   search, to see if there will be any problems during the equation search   related to the host environment.
  * `saved_state=nothing`: If you have already   run `equation_search` and want to resume it, pass the state here.   To get this to work, you need to have set return*state=true,   which will cause `equation*search` to return the state. The second   element of the state is the regular return value with the hall of fame.   Note that you cannot change the operators or dataset, but most other options   should be changeable.
  * `return_state::Union{Bool, Nothing}=nothing`: Whether to return the   state of the search for warm starts. By default this is false.
  * `loss_type::Type=Nothing`: If you would like to use a different type   for the loss than for the data you passed, specify the type here.   Note that if you pass complex data `::Complex{L}`, then the loss   type will automatically be set to `L`.
  * `verbosity`: Whether to print debugging statements or not.
  * `logger::Union{AbstractSRLogger,Nothing}=nothing`: An optional logger to record   the progress of the search. You can use an `SRLogger` to wrap a custom logger,   or pass `nothing` to disable logging.
  * `progress`: Whether to use a progress bar output. Only available for   single target output.
  * `X_units::Union{AbstractVector,Nothing}=nothing`: The units of the dataset,   to be used for dimensional constraints. For example, if `X_units=["kg", "m"]`,   then the first feature will have units of kilograms, and the second will   have units of meters.
  * `y_units=nothing`: The units of the output, to be used for dimensional constraints.   If `y` is a matrix, then this can be a vector of units, in which case   each element corresponds to each output feature.

# Returns

  * `hallOfFame::HallOfFame`: The best equations seen during the search.   hallOfFame.members gives an array of `PopMember` objects, which   have their tree (equation) stored in `.tree`. Their loss   is given in `.loss`. The array of `PopMember` objects   is enumerated by size from `1` to `options.maxsize`.
