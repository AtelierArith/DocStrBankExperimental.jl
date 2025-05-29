```
p = plot_seqd(seq::Sequence; sampling_params=KomaMRIBase.default_sampling_params())
```

Plots a sampled sequence struct.

# Arguments

  * `seq`: (`::Sequence`) Sequence struct

# Keywords

  * `sampling_params`: (`::Dict{String,Any}()`, `=KomaMRIBase.default_sampling_params()`) dictionary of   sampling parameters

# Returns

  * `p`: (`::PlotlyJS.SyncPlot`) plot of the sampled Sequence struct

# Examples

```julia-repl
julia> seq_file = joinpath(dirname(pathof(KomaMRI)), "../examples/1.sequences/spiral.seq")

julia> seq = read_seq(seq_file)

julia> plot_seqd(seq)
```
