```
p = plot_kspace(seq::Sequence; width=nothing, height=nothing, darkmode=false)
```

Plots the k-space of a Sequence struct.

# Arguments

  * `seq`: (`::Sequence`) Sequence struct

# Keywords

  * `width`: (`::Integer`, `=nothing`) plot width
  * `height`: (`::Integer`, `=nothing`) plot height
  * `darkmode`: (`::Bool`, `=false`) boolean to indicate whether to display darkmode style

# Returns

  * `p`: (`::PlotlyJS.SyncPlot`) plot of the k-space of the Sequence struct

# Examples

```julia-repl
julia> seq_file = joinpath(dirname(pathof(KomaMRI)), "../examples/1.sequences/spiral.seq")

julia> seq = read_seq(seq_file)

julia> plot_kspace(seq)
```
