```
iers_precession(m::IERSModel, tt_c::Number)
```

`tt_c`で表される時間において、MEME2000軸から平均日（MOD）軸へのベクトルを回転させる前進行列を返します。この時間は、`J2000`からのTTジュリア世紀で表されます。IERSの規約`m`に従います。

!!! note
    この行列は、J2000の平均赤道および平均春分点（MEME2000）から平均日（MOD）軸へのベクトルを回転させます。GCRFとMEME2000の間のフレームバイアスは返される行列から除外されており、別の回転で最終的に含める必要があります。


!!! note
    IAUの前進と黄道に関する作業部会（Hilton, 2006）は、前進角のパラメータ化の選択をユーザーに委ねることを決定しました。この関数では、IERS 1996の規約に対して、前進行列はNewcombとLiekseの伝統的なパラメータ化（`zₐ`、`θₐ`、`ζₐ`）を使用して計算されますが、残りのモデルには（Capitaine et al., 2003a）によって推奨される4角度の定式化（`ϵ₀`、`ψₐ`、`ωₐ`、`χₐ`）を採用しています。


### 参考文献

  * Lieske J. H. et al, (1977), IAU（1976）天文定数システムに基づく前進量の表現。
  * Hilton J. L. et al., (2006), 国際天文学連合第I部門の前進と黄道に関する作業部会の報告。
  * Capitaine N. et al., (2003a), IAU 2000前進量の表現。
  * IERS技術ノート No. [21](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn21.html)
  * IERS技術ノート No. [32](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn32.html)
  * IERS技術ノート No. [36](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn36.html)

### 参照

[`precession_angles_rot3`](@ref)および[`precession_angles_rot4`](@ref)も参照してください。
