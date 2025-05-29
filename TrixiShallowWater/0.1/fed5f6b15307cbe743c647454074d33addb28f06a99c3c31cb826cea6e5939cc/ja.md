```
min_max_speed_chen_noelle(u_ll, u_rr, orientation::Integer,
                          equations::ShallowWaterEquations2D)
min_max_speed_chen_noelle(u_ll, u_rr, normal_direction::AbstractVector,
                          equations::ShallowWaterEquations2D)
```

浅水方程の左状態と右状態 `u_ll, u_rr` の最小および最大波速の特別な推定。これらの近似速度は、HLL型数値フラックス [`flux_hll_chen_noelle`](@ref) に使用されます。これらの波速の推定値は、特定の静水圧再構成技術とともに、数値フラックスが正であり、エントロピー不等式を満たすことを保証します。

この静水圧再構成とその動機に関する詳細は、以下の参考文献に記載されています。波速の定義は式 (2.20) に示されています。

  * Guoxian Chen and Sebastian Noelle (2017) A new hydrostatic reconstruction scheme based on subcell reconstructions [DOI:10.1137/15M1053074](https://dx.doi.org/10.1137/15M1053074)
