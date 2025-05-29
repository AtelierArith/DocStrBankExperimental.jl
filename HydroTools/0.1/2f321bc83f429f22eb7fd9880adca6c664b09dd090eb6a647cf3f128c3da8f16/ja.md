```
cal_Rln_yang2019(Tₛ, Rsi, Rsi_toa; lat=30, ϵ::Float64=0.96, n1=2.52, n2=2.37, n3=0.035)
```

ヤンら（2019）の方法に基づいて長波放射を計算します。

# 引数

  * `Ts`: 陸面温度。
  * `Rsi`: 表面に入射する短波放射。
  * `Rsi_toa`: 大気上部での入射短波放射。
  * `lat`: 緯度（度単位）。デフォルトは30。
  * `ϵ`: 放射率。デフォルトは0.96。
  * `n1`, `n2`, `n3`: `ΔT`のパラメータ。詳細はヤン2019を参照。

# 参考文献

1. Yang, Y., & Roderick, M. L. (2019). Radiation, surface temperature and evaporation over wet surfaces. Quarterly Journal of the Royal Meteorological Society, 145(720), 1118–1129. https://doi.org/10.1002/qj.3481
2. Tu, Z., & Yang, Y. (2022). On the Estimation of Potential Evaporation Under Wet and Dry Conditions. Water Resources Research, 58(4). https://doi.org/10.1029/2021wr031486
