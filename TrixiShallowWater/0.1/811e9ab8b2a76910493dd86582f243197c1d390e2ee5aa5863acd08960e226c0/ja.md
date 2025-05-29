```
flux_es_ersing_etal(u_ll, u_rr, orientation_or_normal_direction,
                    equations::ShallowWaterTwoLayerEquations2D)
```

二層浅水方程式のエントロピー安定表面フラックス。エントロピー保存型の [`flux_wintermeyer_etal`](@ref) を使用し、エントロピー変数のジャンプに依存するラックス-フリードリヒス型の減衰を追加します。

詳細については、以下を参照してください：

  * Patrick Ersing, Andrew R. Winters (2023) An entropy stable discontinuous Galerkin method for the two-layer shallow water equations on  curvilinear meshes [DOI: 10.1007/s10915-024-02451-2](https://doi.org/10.1007/s10915-024-02451-2)
