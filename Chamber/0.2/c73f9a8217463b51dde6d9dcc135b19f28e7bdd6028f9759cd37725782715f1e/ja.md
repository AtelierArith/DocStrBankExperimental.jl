```
find_liq(composition::Mafic, water::Float64, co2::Float64, P::Float64, ini_eps_x::Float64)::Float64
```

マグマ中のH2OとCO2の重量分率、および圧力を考慮して、マグマが結晶化し、所望の結晶体積分率に達する温度を求めます。この関数は、融解曲線のパラメータと誤差関数を使用して、液相温度を推定します。

## 引数

  * `composition`: `Mafic()`
  * `water`: マグマ中のH2Oの重量分率。
  * `co2`: マグマ中のCO2の重量分率。
  * `P`: 圧力 (Pa)
  * `ini_eps_x`: 結晶の初期体積分率。

## 戻り値

  * `Tl`: 推定された液相温度 (K)。
