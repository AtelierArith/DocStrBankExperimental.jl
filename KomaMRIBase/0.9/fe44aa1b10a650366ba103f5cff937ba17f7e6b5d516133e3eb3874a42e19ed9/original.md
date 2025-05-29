```
gr = Grad(A, T)
gr = Grad(A, T, rise)
gr = Grad(A, T, rise, delay)
gr = Grad(A, T, rise, fall, delay)
gr = Grad(A, T, rise, fall, delay, first, last)
```

The Grad struct represents a gradient of a sequence event.

# Arguments

  * `A`: (`::Real` or `::Vector`, `[T/m]`) amplitude of the gradient
  * `T`: (`::Real` or `::Vector`, `[s]`) duration of the flat-top
  * `rise`: (`::Real`, `[s]`) duration of the rise
  * `fall`: (`::Real`, `[s]`) duration of the fall
  * `delay`: (`::Real`, `[s]`) duration of the delay

# Returns

  * `gr`: (`::Grad`) gradient struct

# Examples

```julia-repl
julia> gr = Grad(1, 1, 0.1, 0.1, 0.2)

julia> seq = Sequence([gr]); plot_seq(seq)
```
