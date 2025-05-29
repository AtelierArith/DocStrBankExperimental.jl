```
flux_winters_etal(u_ll, u_rr, orientation_or_normal_direction,
                  equations::PolytropicEulerEquations2D)
```

等温または多様体ガスのためのエントロピー保存二点フラックス。ここで示される密度の評価には特別な重み付きストラルスキー平均 `stolarsky_mean` が必要です。`gamma = 1` の等温ガスの場合、この `stolarsky_mean` は [`ln_mean`](@ref) になります。

詳細については、以下の参考文献のセクション3.2を参照してください。

  * Andrew R. Winters, Christof Czernik, Moritz B. Schily & Gregor J. Gassner (2020) Entropy stable numerical approximations for the isothermal and polytropic Euler equations [DOI: 10.1007/s10543-019-00789-w](https://doi.org/10.1007/s10543-019-00789-w)
