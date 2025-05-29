```
InPhaseSpacePoint(
    proc::AbstractProcessDefinition,
    model::AbstractModelDefinition,
    psl::AbstractPhaseSpaceLayout,
    in_coords::NTuple{N,Real},
)
```

与えられた座標から `_generate_momenta` インターフェースを使用して [`PhaseSpacePoint`](@ref) を構築します。結果は `<: InPhaseSpacePoint` ですが、**<: OutPhaseSpacePoint** ではありません。

!!! note
    座標からの [`OutPhaseSpacePoint`](@ref) に対する類似の関数は存在せず、完全な [`PhaseSpacePoint`](@ref) のみです。

