```
p = plot_M1(seq::Sequence; kwargs...)
```

Plots the first order moment (M1) of a Sequence struct.

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

# Returns

  * `p`: (`::PlotlyJS.SyncPlot`) plot of the moment M1 of the Sequence struct

# Examples

```julia-repl
julia> seq_file = joinpath(dirname(pathof(KomaMRI)), "../examples/1.sequences/spiral.seq")

julia> seq = read_seq(seq_file)

julia> plot_M1(seq)
```
