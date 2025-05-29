```julia
formalism(
    file::PseudoPotentialIO.PsPFile
) -> Union{Type{PseudoPotentialIO.NormConservingPsP}, Type{PseudoPotentialIO.ProjectorAugmentedWavePsP}, Type{PseudoPotentialIO.UltrasoftPsP}}

```

擬ポテンシャルの形式。

```julia
formalism(file)
```

は[`packages/PseudoPotentialIO/YkY3g/src/file/file.jl:105`](file:///home/terasaki/.julia/packages/PseudoPotentialIO/YkY3g/src/file/file.jl)で定義されています。
