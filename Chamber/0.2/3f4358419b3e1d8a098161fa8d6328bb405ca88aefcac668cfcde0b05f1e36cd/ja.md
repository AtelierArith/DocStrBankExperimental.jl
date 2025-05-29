```
crystal_fraction(composition::Mafic, T::Float64, P::Float64, mH2O::Float64, mCO2::Float64)::NamedTuple{(:eps_x, :deps_x_dP, :deps_x_dT, :deps_x_deps_g, :deps_x_dmco2_t, :deps_x_dmh2o_t), NTuple{6, Float64}}
```

与えられた温度、圧力、水分およびCO2含量におけるマグマ中の結晶体積分率とその導関数を計算します。

## 引数

  * `composition`: `Mafic()`
  * `T`: 温度 (K)
  * `P`: 圧力 (Pa)
  * `mH2O`: マグマ中のH2Oの重量分率。
  * `mCO2`: マグマ中のCO2の重量分率。

## 戻り値

以下のフィールドを持つNamedTupleを返します：

  * `eps_x`: 結晶体積分率。
  * `deps_x_dP`: 圧力に対するeps_xの導関数。
  * `deps_x_dT`: 温度に対するeps_xの導関数。
  * `deps_x_deps_g`: ガス体積分率に対するeps_xの導関数。
  * `deps_x_dmco2_t`: CO2含量に対するeps_xの導関数。
  * `deps_x_dmh2o_t`: H2O含量に対するeps_xの導関数。
