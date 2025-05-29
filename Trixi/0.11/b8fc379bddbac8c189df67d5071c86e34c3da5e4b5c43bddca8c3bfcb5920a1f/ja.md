```
hydrostatic_reconstruction_audusse_etal(u_ll, u_rr, orientation_or_normal_direction,
                                        equations::ShallowWaterEquations2D)
```

水位の静水圧再構成の特定のタイプで、一般的な底面地形 [`ShallowWaterEquations2D`](@ref) に対してバランスの取れた状態を保証します。再構成された解の状態 `u_ll_star` と `u_rr_star` 変数は、インターフェースでの表面数値フラックスを評価するために使用されます。一般的な数値フラックスルーチン [`FluxHydrostaticReconstruction`](@ref) と組み合わせて使用します。

静水圧再構成の詳細とその動機については、以下を参照してください。

  * Emmanuel Audusse, François Bouchut, Marie-Odile Bristeau, Rupert Klein, and Benoit Perthame (2004) A fast and stable well-balanced scheme with hydrostatic reconstruction for shallow water flows [DOI: 10.1137/S1064827503431090](https://doi.org/10.1137/S1064827503431090)
