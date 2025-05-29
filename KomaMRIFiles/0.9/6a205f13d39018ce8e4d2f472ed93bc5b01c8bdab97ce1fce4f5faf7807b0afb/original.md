```
seq = read_seq(filename)
```

Returns the Sequence struct from a Pulseq file with `.seq` extension.

# Arguments

  * `filename`: (`::String`) absolute or relative path of the sequence file `.seq`

# Returns

  * `seq`: (`::Sequence`) Sequence struct

# Examples

```julia-repl
julia> seq_file = joinpath(dirname(pathof(KomaMRI)), "../examples/1.sequences/spiral.seq")

julia> seq = read_seq(seq_file)

julia> plot_seq(seq)
```
