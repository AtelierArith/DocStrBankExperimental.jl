```
rf = RF(A, T)
rf = RF(A, T, Δf)
rf = RF(A, T, Δf, delay)
```

The RF struct represents a Radio Frequency excitation of a sequence event.

# Arguments

  * `A`: (`::Complex`, `[T]`) RF complex amplitud modulation (AM), $B_1(t) = |B_1(t)|   e^{i\phi(t)} = B_{1}(t) + iB_{1,y}(t)$
  * `T`: (`::Real`, [`s`]) RF duration
  * `Δf`: (`::Real` or `::Vector`, [`Hz`]) RF frequency difference with respect to the Larmor frequency.   This can be a number but also a vector to represent frequency modulated signals (FM).
  * `delay`: (`::Real`, [`s`]) RF delay time

# Returns

  * `rf`: (`::RF`) the RF struct

# Examples

```julia-repl
julia> rf = RF(1, 1, 0, 0.2)

julia> seq = Sequence(); seq += rf; plot_seq(seq)
```
