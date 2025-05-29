```
process_each_export(f, vtk_path; kwargs...)
process_each_export(f, job; kwargs...)
```

A function for postprocessing every exported file. This function works with multithreading and MPI and determines the backend exactly like the [`submit`](@ref) function.

# Arguments

  * `f::Function`: The processing function with signature `f(r0, r, id)`.

      * `r0`: The results of [`read_vtk`](@ref) for the exported file of the reference   results.
      * `r`: The results of [`read_vtk`](@ref) for a time step.
      * `id::Ind`: An ID indicating the number of the exported file (counted from 1, starting   with the reference file).
  * `vtk_path::AbstractString`: A path that should contain the export results of a simulation.
  * `job::Job`: A job object. The path of the VTK files will then be processed from the   job options.

# Keywords

  * `serial::Bool`: If `true`, all results will be processed in the correct order of the time   steps and on a single thread, cf. the MPI root rank.
