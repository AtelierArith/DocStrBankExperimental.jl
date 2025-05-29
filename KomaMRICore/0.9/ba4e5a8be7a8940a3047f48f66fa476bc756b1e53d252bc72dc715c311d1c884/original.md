```
out = simulate(obj::Phantom, seq::Sequence, sys::Scanner; sim_params, w)
```

Returns the raw signal or the last state of the magnetization according to the value of the `"return_type"` key of the `sim_params` dictionary. 

This is a wrapper function to `run_sim_time_iter`, which converts the inputs to the appropriate types and discretizes the sequence before simulation. The reported simulation time only considers `run_sim_time_iter`, as the preprocessing duration should be negligible compared to the simulation time (if this is not the case, please file a bug report). 

# Arguments

  * `obj`: (`::Phantom`) Phantom struct
  * `seq`: (`::Sequence`) Sequence struct
  * `sys`: (`::Scanner`) Scanner struct

# Keywords

  * `sim_params`: (`::Dict{String,Any}`, `=Dict{String,Any}()`) simulation parameter dictionary
  * `w`: (`::Blink.AtomShell.Window`, `=nothing`) the window within which to display a   progress bar in the Blink Window UI. If this variable is anything other than 'nothing',   the progress bar will be considered

# Returns

  * `out`: (`::Vector{Complex}` or `::SpinStateRepresentation` or `::RawAcquisitionData`) depending   on whether "return_type" is "mat", "state" or "raw" (default), respectively

# Examples

```julia-repl
julia> seq_file = joinpath(dirname(pathof(KomaMRI)), "../examples/5.koma_paper/comparison_accuracy/sequences/EPI/epi_100x100_TE100_FOV230.seq");

julia> sys, obj, seq = Scanner(), brain_phantom2D(), read_seq(seq_file)

julia> raw = simulate(obj, seq, sys)

julia> plot_signal(raw)
```
