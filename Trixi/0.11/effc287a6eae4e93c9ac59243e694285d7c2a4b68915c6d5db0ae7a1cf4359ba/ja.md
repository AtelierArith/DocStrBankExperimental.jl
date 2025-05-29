```
hydrostatic_reconstruction_audusse_etal(u_ll, u_rr, orientation::Integer,
                                        equations::ShallowWaterEquations1D)
```

水位の静水圧再構成の特定のタイプで、一般的な底面地形 [`ShallowWaterEquations1D`](@ref) に対してバランスの取れた状態を保証します。再構成された解の状態 `u_ll_star` と `u_rr_star` 変数は、界面での表面数値フラックスを評価するために使用されます。一般的な数値フラックスルーチン [`FluxHydrostaticReconstruction`](@ref) と組み合わせて使用します。

この静水圧再構成とその動機に関する詳細は以下にあります。

  * Emmanuel Audusse, François Bouchut, Marie-Odile Bristeau, Rupert Klein, and Benoit Perthame (2004) A fast and stable well-balanced scheme with hydrostatic reconstruction for shallow water flows [DOI: 10.1137/S1064827503431090](https://doi.org/10.1137/S1064827503431090)
