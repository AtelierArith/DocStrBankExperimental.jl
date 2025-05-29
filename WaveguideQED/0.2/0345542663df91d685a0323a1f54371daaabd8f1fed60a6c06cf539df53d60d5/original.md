```
get_waveguide_location(basis::WaveguideBasis)
get_waveguide_location(basis::CompositeBasis)
```

Return index of [`WaveguideBasis`](@ref) location in Hilbert space of basis b. `Btotal = waveguidebasis ⊗ otherbasis` where waveguidebasis is a [`WaveguideBasis`](@ref) and `otherbasis` some other basis then `get_waveguide_location(Btotal)` returns 1.  While `Btotal = otherbasis ⊗ waveguidebasis` with `get_waveguide_location(Btotal)` returns 2.
