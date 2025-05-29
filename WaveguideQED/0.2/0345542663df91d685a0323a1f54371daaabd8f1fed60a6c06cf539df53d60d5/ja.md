```
get_waveguide_location(basis::WaveguideBasis)
get_waveguide_location(basis::CompositeBasis)
```

[`WaveguideBasis`](@ref) の位置を基底 b のヒルベルト空間内で返します。`Btotal = waveguidebasis ⊗ otherbasis` で、waveguidebasis は [`WaveguideBasis`](@ref) であり、`otherbasis` は他の基底である場合、`get_waveguide_location(Btotal)` は 1 を返します。一方、`Btotal = otherbasis ⊗ waveguidebasis` の場合、`get_waveguide_location(Btotal)` は 2 を返します。
