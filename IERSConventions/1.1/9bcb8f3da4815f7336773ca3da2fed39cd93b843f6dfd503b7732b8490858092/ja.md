```
cip_xys(m::IERSModel, tt_c::Number, δX::Number=0, δY::Number=0)
```

IERSの規則に従って、時刻`tt_c`におけるCIP X、YおよびCIOロケータsの座標をラジアンで計算します。`TT`のジュリア世紀でJ2000からの経過時間を表します。オプションのEOP摂動補正は、`δX`および`δY`パラメータを介して提供できます。

!!! note
    CIP補正の小さな値のため、CIOロケータはそれらにほとんど影響を受けません。実際、一部の報告書では補正されたCIP座標で`s`を計算し、一部ではそうしません。


### 参考文献

  * Capitaine N. and Wallace P. T. (2008), Concise CIO based precession-nutation formulations
  * IERS Technical Note No. [21](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn21.html)
  * IERS Technical Note No. [32](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn32.html)
  * IERS Technical Note No. [36](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn36.html)

### さらに見る

[`iers_cip_motion`](@ref)および[`cip_xy`](@ref)も参照してください。
