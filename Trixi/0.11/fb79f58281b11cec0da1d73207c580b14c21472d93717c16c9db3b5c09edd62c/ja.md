```
flux_fjordholm_etal(u_ll, u_rr, orientation,
                    equations::ShallowWaterEquations1D)
```

全エネルギー保存（浅水方程式の数学的エントロピー）。底面の地形がゼロでない場合、これは表面フラックスとしてのみ使用するべきであり、さもなければスキームはバランスが取れなくなります。体積フラックスのバランスを保つためには [`flux_wintermeyer_etal`](@ref) を使用してください。

詳細は論文の式 (4.1) にあります：

  * Ulrik S. Fjordholm, Siddhartha Mishra and Eitan Tadmor (2011) Well-balanced and energy stable schemes for the shallow water equations with discontinuous topography [DOI: 10.1016/j.jcp.2011.03.042](https://doi.org/10.1016/j.jcp.2011.03.042)
