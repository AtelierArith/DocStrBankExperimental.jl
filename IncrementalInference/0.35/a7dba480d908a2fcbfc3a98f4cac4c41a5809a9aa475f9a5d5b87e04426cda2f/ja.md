```julia
checkGradientsToleranceMask(fgc; ...)
checkGradientsToleranceMask(fgc, J; tol)

```

勾配行列 `J` と同じサイズのマスクを返し、どの要素が期待される感度閾値 `tol` を超えているかを示します。

ノート

  * 閾値の精度は2つの部分に依存します、

      * 数値勾配摂動サイズ `fgc._h`,
      * 残差因子が計算される精度許容値（ここでは制御されていません）
