```
トレンチ構造
```

トレンチとスラブのジオメトリを定義する構造。

# パラメータ

  * `Start`     - トレンチの開始点（`x`,`y`）座標
  * `End`       - トレンチの終了点（`x`,`y`）座標
  * `n_seg`     - スラブが傾斜に沿って離散化されるセグメントの数
  * `Length`    - スラブの長さ
  * `Thickness` - スラブの厚さ
  * `Lb`        - 曲げ角度関数を適用するための臨界距離 Lb ∈ [0,Length];
  * `θ_max`     - 最大曲げ角度 ∈ [0°,90°]。
  * `direction` - 傾斜の方向              座標系の回転は、新しいXがセグメントに平行になるように行われます。              回転は反時計回りであるため、座標yには特定の値があります：directionは、沈み込みが新しいy座標系の正の方向または負の方向に向かっているかを示します。 実際には、yに-1または+1を掛けることで追加の変換を適用します;
  * `d_decoupling` - スラブが完全にマントルに沈む深さ。
  * `type_bending` - スラブの曲げ角度のタイプ [`:Linear`, `:Ribe`].   スラブの角度は、トレンチからのスラブの長さに沿った実際の距離 `l` (∈ [0,Length]) の関数として変化します。   場合によっては：       - `:Linear`           `math θ(l) = ((θ_max - 0.0)/(Lb-0))*l`;       - `:Ribe`           `math θ(l) =  θ_max*l^2*((3*Lb-2*l))/(Lb^3)`;           これはRibe 2010 [Bending mechanics and mode selection in free subduction: a thin-sheet analysis] から取られています。

    l>Lbの場合、θ(l) = θ_max;
  * `WeakzoneThickness` - ウィークゾーンの厚さ [km]
  * `WeakzonePhase` - ウィークゾーンの相
