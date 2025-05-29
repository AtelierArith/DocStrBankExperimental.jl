```
Job(name::String, structure::Structure;
      calculations      ::Vector{Calculation} = Calculation[],
      dir               ::String = pwd(),
      version           ::Int = last_job_version(dir),
      copy_temp_folders ::Bool = false, 
      server            ::String = getdefault_server(),
      environment::String ="")
```

A [`Job`](@ref) embodies a set of [`Calculations`](@ref Calculation) to be ran in directory `dir`, with the [`Structure`](@ref) as the subject.

## Keywords/further attributes

  * `calculations`: calculations to calculations that will be run sequentially.
  * `dir`: the directory where the calculations will be run.
  * `version`: the current version of the job.
  * `copy_temp_folders`: whether or not the temporary directory associated with intermediate calculation results should be copied when storing a job version. *CAUTION* These can be quite large.
  * `server`: [`Server`](@ref) where to run the [`Job`](@ref).
  * `environment`: [`Environment`](@ref) to be used for running the [`Job`](@ref).

```
Job(job_name::String, structure::Structure, calculations::Vector{<:Calculation}, common_flags::Pair{Symbol, <:Any}...; kwargs...)
```

Creates a new job. The common flags will be attempted to be set in each of the `calculations`. The `kwargs...` are passed to the [`Job`](@ref) constructor. 

```
Job(job_dir::String, job_script="job.sh"; version=nothing, kwargs...)
```

Loads the job in the `dir`. If `job_dir` is not a valid job path, the previously saved jobs will be scanned for a job with a `dir` that partly includes `job_dir`. If `version` is specified the corresponding job version will be returned if it exists.  The `kwargs...` will be passed to the [`Job`](@ref) constructor.
