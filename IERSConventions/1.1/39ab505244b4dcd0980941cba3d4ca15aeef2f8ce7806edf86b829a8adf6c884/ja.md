```
cip_xy(m::IERSModel, tt_c::Number)
```

IERSの規約`m`に従って、時刻`tt_c`におけるCIP XおよびY座標をラジアンで計算します。これはJ2000からの`TT`ユリウス世紀で表現されます。

!!! warning
    自由コアの歳差と時間依存効果の計算はこのモデルから除外されています。IAU 2006/2000 A歳差-歳差モデルで< 1μasの精度を達成するには、IERS EOPデータを使用して、これらの効果を事後的に（δXおよびδYを通じて）含める必要があります。


### 参考文献

  * Capitaine N. and Wallace P. T. (2008), Concise CIO based precession-nutation formulations.
  * IERS Technical Note No. [21](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn21.html)
  * IERS Technical Note No. [32](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn32.html)
  * IERS Technical Note No. [36](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn36.html)

### 参照

[`iers_cip_motion`](@ref)および[`cip_xys`](@ref)も参照してください。
