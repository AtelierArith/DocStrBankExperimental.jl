```
ws, states = simulate_mrst_case(file_name)
simulate_mrst_case(file_name; <keyword arguments>)
```

Simulate a MRST case from `file_name` as exported by `writeJutulInput` in MRST.

# Arguments

  * `file_name::String`: The path to a `.mat` or `.data` file that is to be simulated.

# Keyword arguments

  * `extra_outputs::Vector{Symbol} = [:Saturations]`: Additional variables to output from the simulation.
  * `write_output::Bool = true`: Write output (in the default JLD2 format)
  * `output_path = nothing`: Directory for output files. Files will be written under this directory. Defaults to the folder of `file_name`.
  * `write_mrst = true`: Write MRST compatible output after completed simulation that can be read by `readJutulOutput` in MRST.
  * `backend=:csc`: choice of backend for linear systems. `:csc` for default Julia sparse, `:csr` for experimental parallel CSR.
  * `verbose=true`: print some extra information specific to this routine upon calling
  * `nthreads=Threads.nthreads()`: number of threads to use
  * `linear_solver=:bicgstab`: name of Krylov.jl solver to use, or :direct (for small cases only)
  * `info_level=0`: standard Jutul info_level. 0 for minimal printing, -1 for no printing, 1-5 for various levels of verbosity

Additional input arguments are passed onto, [`setup_case_from_mrst`](@ref), [`setup_reservoir_simulator`](@ref) and [`simulator_config`](@ref) if applicable.
