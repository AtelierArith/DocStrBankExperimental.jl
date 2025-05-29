```
gr = Grad(f::Function, T::Real, N::Integer; delay::Real)
```

Generates an arbitrary gradient waveform defined by the function `f` in the interval t ∈ [0,`T`]. The time separation between two consecutive samples is given by T/(N-1).

# Arguments

  * `f`: (`::Function`) function that describes the gradient waveform
  * `T`: (`::Real`, `[s]`) duration of the gradient waveform
  * `N`: (`::Integer`, `=300`) number of samples of the gradient waveform

# Keywords

  * `delay`: (`::Real`, `=0`, `[s]`) delay time of the waveform

# Returns

  * `gr`: (`::Grad`) gradient struct

# Examples

```julia-repl
julia> gx = Grad(t -> sin(π*t / 0.8), 0.8)

julia> seq = Sequence([gx]); plot_seq(seq)
```
