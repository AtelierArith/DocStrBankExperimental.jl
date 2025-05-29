```
dissipation_roe(u_ll, u_rr, orientation_or_normal_direction,
                                equations::ShallowWaterEquationsWetDry1D)
```

[`ShallowWaterEquationsWetDry1D`](@ref) のためのロエ型散逸項。この散逸項は、[`Trixi.flux_central`](@extref) と組み合わせて、古典的なロエソルバーを作成することができます。 

ロエ線形化の詳細については、書籍の1次元浅水方程式に関する第15.3.2章および第15.3.3章を参照してください：

  * Randall J. LeVeque (2002) Finite Volume Methods for Hyperbolic Problems [DOI: 10.1017/CBO9780511791253](https://doi.org/10.1017/CBO9780511791253)
