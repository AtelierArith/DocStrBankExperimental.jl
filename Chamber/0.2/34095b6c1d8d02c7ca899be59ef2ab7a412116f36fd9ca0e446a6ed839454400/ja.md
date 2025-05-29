```
parameters_melting_curve(composition::Mafic, mH2O::Float64, mCO2::Float64, P::Float64)::NamedTuple{(:a, :dadx, :dady, :dadz, :b, :dbdx, :dbdy, :dbdz), NTuple{8, Float64}}
```

  * この関数は `find_liq`、`crystal_fraction`、`crystal_fraction_eps_x` 関数内で使用されます。

## 引数

  * `composition`: `Mafic()`
  * `mH2O`: マグマ中のH2Oの重量比。
  * `mCO2`: マグマ中のCO2の重量比。
  * `P`: 圧力 (Pa)
