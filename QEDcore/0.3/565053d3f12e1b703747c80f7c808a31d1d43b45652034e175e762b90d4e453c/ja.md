```
PhaseSpacePoint(
    proc::AbstractProcessDefinition,
    model::AbstractModelDefinition,
    psl::AbstractPhaseSpaceLayout,
    in_coords::NTuple{N,Real},
    out_coords::NTuple{M,Real},
)
```

与えられた座標から `_generate_momenta` インターフェースを使用して [`PhaseSpacePoint`](@ref) を構築します。
