```
hydrostatic_reconstruction_ersing_etal(u_ll, u_rr, equations::ShallowWaterMultiLayerEquations1D)
```

水位と底面地形の特定の静水圧再構成により、湿潤/乾燥遷移の存在下でのバランスの良さと、[`ShallowWaterMultiLayerEquations1D`](@ref)のエントロピー安定性を保証します。 再構成された解の状態 `u_ll_star` と `u_rr_star` は、インターフェースでの表面数値フラックスを評価するために使用されます。 重要なアイデアは、底面地形が不連続であることを許可しながら、サブセルを使用して底面地形と水位インターフェースの区分線形再構成を行うことです。 一般的な数値フラックスルーチン [`Trixi.FluxHydrostaticReconstruction`](@extref) と組み合わせて使用します。
