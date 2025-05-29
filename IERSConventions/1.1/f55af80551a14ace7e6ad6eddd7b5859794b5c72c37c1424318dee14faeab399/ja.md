```
iers_gast(m::IERSModel, tt_c::Number, δΔψ::Number=0)
```

グリニッジ見かけの恒星時 (GAST) を計算します。これは、IERSの規約に従い、`m` の時刻 `tt_c` を J2000 からの TT ジュリア世紀で表したものです。緯度の摂動の正確な計算のために、オプションの EOP 補正を `δΔψ` を通じて渡すことができます。

!!! note
    入力時間は、地球回転角 (ERA) の計算や1996年の規約に基づく GMST の計算のために自動的に UT1 に変換されます。したがって、この関数を呼び出す前に EOP データをロードする必要があります。


### 参考文献

  * IERS 技術ノート No. [21](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn21.html)
  * IERS 技術ノート No. [32](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn32.html)
  * IERS 技術ノート No. [36](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn36.html)

### 参照

[`iers_gmst`](@ref)、[`equation_equinoxes`](@ref)、および [`iers_era`](@ref) も参照してください。
