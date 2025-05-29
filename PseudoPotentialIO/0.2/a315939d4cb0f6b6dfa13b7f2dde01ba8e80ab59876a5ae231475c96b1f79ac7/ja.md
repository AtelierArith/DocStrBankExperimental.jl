```julia
formalism(
    psp::PseudoPotentialIO.AbstractPsP
) -> Union{Type{PseudoPotentialIO.NormConservingPsP}, Type{PseudoPotentialIO.ProjectorAugmentedWavePsP}, Type{PseudoPotentialIO.UltrasoftPsP}}

```

擬ポテンシャルの形式（ノルム保存、ウルトラソフト、プロジェクター拡張波、またはクーロン）。

```julia
formalism(psp)
```

[`packages/PseudoPotentialIO/YkY3g/src/psp/psp.jl:287`](file:///home/terasaki/.julia/packages/PseudoPotentialIO/YkY3g/src/psp/psp.jl) で定義されています。
