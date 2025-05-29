```
iers_bias(m::IERSModel, tt_c::Number)
```

フレームバイアス行列を計算し、GCRF軸からJ2000の平均春分点および平均赤道（MEME2000）軸へのベクトルを変換します。

!!! note
    IERS 1996年の規約ではバイアス行列がまだ定義されていなかったため、返される行列は単位行列です。


### 参考文献

  * IERS技術ノート No. [21](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn21.html)
  * IERS技術ノート No. [32](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn32.html)
  * IERS技術ノート No. [36](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn36.html)

### さらに見る

[`iers_precession`](@ref)、[`iers_pb`](@ref)、および[`iers_npb`](@ref)も参照してください。
