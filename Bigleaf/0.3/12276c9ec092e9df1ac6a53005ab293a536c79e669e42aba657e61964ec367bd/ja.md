```
VPD_to_rH(VPD,Tair; ...)
H_to_VPD(rH,Tair; ...)
e_to_rH(e,Tair; ...)
VPD_to_e(VPD,Tair; ...)
e_to_VPD(e,Tair; ...)
e_to_q(e,pressure; ...)
q_to_e(q,pressure; ...)
q_to_VPD(q,Tair,pressure; ...)
VPD_to_q(VPD,Tair,pressure; ...)
```

水蒸気圧 (e)、水蒸気圧不足 (VPD)、比湿 (q)、および相対湿度 (rH) の間の変換。

# 引数

  * Tair:      空気温度 (℃)
  * pressure:  大気圧 (kPa)
  * e:         水蒸気圧 (kPa)
  * q:        比湿 (kg kg-1)
  * VPD:       水蒸気圧不足 (kPa)
  * rH:        相対湿度 (-)

すべての関数は、オプションの引数を受け入れます：

  * `Esat_formula`: [`Esat_from_Tair`](@ref) で使用される式
  * `constants`: [`BigleafConstants`](@ref) からの辞書で、エントリ eps と Pa2kPa を含む

# 参考文献

Foken, T, 2008: Micrometeorology_ Springer, Berlin, Germany.
