```
iers_gmst(m::IERSModel, tt_c::Number)
```

グリニッジ平均恒星時 (GMST) を計算します。これは、IERSの規約に従い、`m` の時刻 `tt_c` を J2000 からの `TT` ジュリアン世紀で表現したものです。

!!! note
    入力時間は、地球回転角 (ERA) の計算や1996年の規約に基づくGMSTの計算のために自動的にUT1に変換されます。したがって、この関数を呼び出す前にEOPデータをロードする必要があります。


### 参考文献

  * IERS技術ノート No. [21](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn21.html)
  * IERS技術ノート No. [32](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn32.html)
  * IERS技術ノート No. [36](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn36.html)

### 参照

[`iers_gast`](@ref) および [`iers_era`](@ref) も参照してください。
