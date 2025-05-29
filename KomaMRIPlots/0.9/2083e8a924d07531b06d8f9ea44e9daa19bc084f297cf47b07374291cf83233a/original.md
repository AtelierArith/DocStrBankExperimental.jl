```
p = plot_signal(raw::RawAcquisitionData; kwargs...)
```

Plots a raw signal in ISMRMRD format.

# Arguments

  * `raw`: (`::RawAcquisitionData`) RawAcquisitionData struct (raw signal in ISMRMRD format)

# Keywords

  * `width`: (`::Integer`, `=nothing`) plot width
  * `height`: (`::Integer`, `=nothing`) plot height
  * `slider`: (`::Bool`, `=true`) boolean to indicate whether to display a slider
  * `show_sim_blocks`: (`::Bool`, `=false`) boolean to indicate whether to display sequence blocks
  * `darkmode`: (`::Bool`, `=false`) boolean to indicate whether to display darkmode style
  * `range`: (`::Vector{Real}`, `=[]`) time range to be displayed initially

# Returns

  * `p`: (`::PlotlyJS.SyncPlot`) plot of the raw signal

# Examples

```julia-repl
julia> seq_file = joinpath(dirname(pathof(KomaMRI)), "../examples/5.koma_paper/comparison_accuracy/sequences/EPI/epi_100x100_TE100_FOV230.seq");

julia> sys, obj, seq = Scanner(), brain_phantom2D(), read_seq(seq_file)

julia> raw = simulate(obj, seq, sys)

julia> plot_signal(raw)
```
