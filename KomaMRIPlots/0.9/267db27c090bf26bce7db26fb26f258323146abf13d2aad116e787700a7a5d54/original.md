```
p = plot_seq(seq::Sequence; kwargs...)
```

Plots a sequence struct.

# Arguments

  * `seq`: (`::Sequence`) Sequence struct

# Keywords

  * `width`: (`::Integer`, `=nothing`) plot width
  * `height`: (`::Integer`, `=nothing`) plot height
  * `slider`: (`::Bool`, `=true`) boolean to indicate whether to display a slider
  * `show_seq_blocks`: (`::Bool`, `=false`) boolean to indicate whether to display sequence blocks
  * `darkmode`: (`::Bool`, `=false`) boolean to indicate whether to display darkmode style
  * `range`: (`::Vector{Real}`, `=[]`) time range to be displayed initially
  * `title`: (`::String`, `=""`) plot title
  * `freq_in_phase`: (`::Bool`, `=true`) Include FM modulation in RF phase
  * `gl`: (`::Bool`, `=false`) use `PlotlyJS.scattergl` backend (faster)
  * `max_rf_samples`: (`::Integer`, `=100`) maximum number of RF samples
  * `show_adc`: (`::Bool`, `=false`) plot ADC samples with markers

# Returns

  * `p`: (`::PlotlyJS.SyncPlot`) plot of the Sequence struct

# Examples

```julia-repl
julia> seq_file = joinpath(dirname(pathof(KomaMRI)), "../examples/1.sequences/spiral.seq")

julia> seq = read_seq(seq_file)

julia> plot_seq(seq)
```
