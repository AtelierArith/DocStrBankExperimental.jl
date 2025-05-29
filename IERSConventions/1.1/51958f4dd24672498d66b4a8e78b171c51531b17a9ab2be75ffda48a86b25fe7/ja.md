```
iers_cip_motion(m::IERSModel, tt_c::Number, δX::Number=0, δY::Number=0)
```

GCRFからCIRFへの回転行列を計算します。これは、IERSの規則 `m` に従い、J2000からのTTジュリア世紀で表された時刻 `tt_c` において行われます。自由コアの歳差運動および時間依存効果に対するオプションのIERS EOP補正は、`δX` および `δY` を介して提供できます。

### 参考文献

  * IERS技術ノート No. [36](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn36.html)

### 参照

[`cip_xy`](@ref) および [`cip_xys`](@ref) も参照してください。
