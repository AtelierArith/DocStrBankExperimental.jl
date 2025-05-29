```
iddata(y,       Ts = nothing)
iddata(y, u,    Ts = nothing)
iddata(y, u, x, Ts = nothing)
```

Create a **time-domain** identification data object. 

# Arguments

  * `y::AbstractArray`: output data (required)
  * `u::AbstractArray`: input data (if available)
  * `x::AbstractArray`: state data (if available)
  * `Ts::Union{Real,Nothing} = nothing`: optional sample time

If the time-series are multivariate, time is in the *last* dimension, i.e., the sizes of the arrays are `(num_variables, num_timepoints)` (see examples below).

# Operations on iddata

  * [`detrend`](@ref)
  * [`prefilter`](@ref)
  * [`resample`](@ref)
  * append two along the time dimension `[d1 d2]` (only do this if the state of the system at the end of `d1` is close to the state at the beginning of `d2`)
  * index time series `d[output_index, input_index]`
  * index the time axis with indices `d[time_indices]`
  * index the time axis with seconds `d[3Sec:12Sec]` (`using ControlSystemIdentification: Sec`)
  * access number of inputs, outputs and sample time: `d.nu, d.ny, d.Ts`
  * access the time time vector `d.t`
  * premultiply to scale outputs `C * d`. Scaling the outputs of a multiple-output system to have roughly the same size is usually recommended before estimating a model in case they have different magnitudes.
  * postmultiply to scale inputs `d * B`
  * [`writedlm`](@ref)
  * [`ramp_in`](@ref), [`ramp_out`](@ref)
  * `plot`
  * [`specplot`](@ref)
  * [`crosscorplot`](@ref)

# Examples

```jldoctest
julia> iddata(randn(10))
Output data of length 10 with 1 outputs, Ts = nothing

julia> iddata(randn(10), randn(10), 1)
InputOutput data of length 10, 1 outputs, 1 inputs, Ts = 1

julia> d = iddata(randn(2, 10), randn(3, 10), 0.1)
InputOutput data of length 10, 2 outputs, 3 inputs, Ts = 0.1

julia> [d d] # Concatenate along time
InputOutput data of length 20, 2 outputs, 3 inputs, Ts = 0.1

julia> d[1:3]
InputOutput data of length 3, 2 outputs, 3 inputs, Ts = 0.1

julia> d.nu
3

julia> d.t # access time vector
0.0:0.1:0.9
```

# Use of multiple datasets

Some estimation methods support the use of multiple datasets to estimate a model. In this case, the datasets are provided as a vector of iddata objects. The methods that currently support this are:

  * [`arx`](@ref)
  * [`era`](@ref)

Several of the other estimation methods can be made to accept multiple datasets with minor modifications.

In some situations, multiple datasets can also be handled by concatenation. For this to be a good idea, the state of the system at the end of one data set must be close to the state at the beginning of the next, e.g., all experiments start and end at the same operating point.
