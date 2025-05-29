```
XYZ0{T1 <: Signed, T2 <: AbstractFloat} <: XYZ{T1, T2}
```

MagNavに必要な最小データセットを含む`XYZ`のサブタイプ。

| **フィールド**  | **型**           | **説明**                             |
|:---------- |:--------------- |:---------------------------------- |
| `info`     | String          | データセット情報                           |
| `traj`     | Traj{`T1`,`T2`} | 軌道構造                               |
| `ins`      | INS{`T1`,`T2`}  | 慣性航法システム構造                         |
| `flux_a`   | MagV{`T2`}      | フラックスAベクトル磁気計測構造                   |
| `flight`   | Vector{`T2`}    | フライト番号                             |
| `line`     | Vector{`T2`}    | 行番号、すなわち`flight`内のセグメント            |
| `year`     | Vector{`T2`}    | 年                                  |
| `doy`      | Vector{`T2`}    | 年の日                                |
| `diurnal`  | Vector{`T2`}    | 測定された日周変動、すなわち時間的変動または宇宙天気の影響 [nT] |
| `igrf`     | Vector{`T2`}    | 国際地磁気基準場（IGRF）、すなわちコアフィールド [nT]    |
| `mag_1_c`  | Vector{`T2`}    | Mag 1 補正済み（クリーン）スカラー磁気計測 [nT]      |
| `mag_1_uc` | Vector{`T2`}    | Mag 1 補正なし（破損）スカラー磁気計測 [nT]        |
