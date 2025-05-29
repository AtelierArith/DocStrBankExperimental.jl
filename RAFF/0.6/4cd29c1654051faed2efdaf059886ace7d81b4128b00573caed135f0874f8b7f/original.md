```
praff(model::Function, data::Array{Float64, 2}, n::Int; kwargs...)

praff(model::Function, gmodel!::Function, data::Array{Float64, 2},
    n::Int; MAXMS::Int=1, SEEDMS::Int=123456789, batches::Int=1,
    initguess::Vector{Float64}=zeros(Float64, n),
    ε::Float64=1.0e-4, noutliers::Int=-1, ftrusted::Union{Float64,
    Tuple{Float64, Float64}}=0.5)
```

Multicore distributed version of RAFF. See the description of the [`raff`](@ref) function for the main (non-optional) arguments. All the communication is performed by channels.

This function uses all available **local** workers to run RAFF algorithm. Note that this function does not use *Tasks*, so all the parallelism is based on the [Distributed](https://docs.julialang.org/en/latest/manual/parallel-computing/#Multi-Core-or-Distributed-Processing-1) package.

The optional arguments are

  * `MAXMS`: number of multistart points to be used
  * `SEEDMS`: integer seed for random multistart points
  * `batches`: size of batches to be send to each worker
  * `initguess`: starting point to be used in the multistart procedure
  * `ε`: stopping tolerance
  * `noutliers`: integer describing the maximum expected number of outliers. The default is *half*. *Deprecated*.
  * `ftrusted`: float describing the minimum expected percentage of trusted points. The default is *half* (0.5). Can also be a Tuple of the form `(fmin, fmax)` percentages of trusted points.

Returns a [`RAFFOutput`](@ref) object containing the solution.
