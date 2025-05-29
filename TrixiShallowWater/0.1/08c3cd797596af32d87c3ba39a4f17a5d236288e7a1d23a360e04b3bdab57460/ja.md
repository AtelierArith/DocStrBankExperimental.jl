```
hydrostatic_reconstruction_chen_noelle(u_ll, u_rr, orientation::Integer,
                                       equations::ShallowWaterEquationsWetDry1D)
```

水位の静水圧再構成の特定のタイプで、[`ShallowWaterEquationsWetDry1D`](@ref)の一般的な底面地形に対してバランスの取れた状態を保証します。再構成された解の状態 `u_ll_star` と `u_rr_star` 変数は、インターフェースでの表面数値フラックスを評価するために使用されます。重要なアイデアは、サブセルを使用してインターフェースでの底面と水位の線形再構成です。一般的な数値フラックスルーチン [`Trixi.FluxHydrostaticReconstruction`](@extref) と組み合わせて使用します。

この静水圧再構成とその動機に関する詳細は以下にあります。

  * Guoxian Chen and Sebastian Noelle (2017) A new hydrostatic reconstruction scheme based on subcell reconstructions [DOI:10.1137/15M1053074](https://dx.doi.org/10.1137/15M1053074)
