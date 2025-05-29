```
conditionalITE(nothing, nothing, tyLS, yNoise, yScale, nothing, nothing, T, Y, doT)
conditionalITE(nothing, xyLS, tyLS, yNoise, yScale, nothing, X, T, Y, doT)
conditionalITE(uyLS, nothing, tyLS, yNoise, yScale, U, nothing, T, Y, doT)
conditionalITE(uyLS, xyLS, tyLS, yNoise, yScale, U, X, T, Y, doT)
```

条件付き個別治療推定

`conditionalITE`は、個別治療効果を生成するために、パラメータ（おそらく事後推論から）と観測データおよび推定データを受け取ります。

パラメータ:

  * `uyLS`: （オプション）潜在的交絡因子から結果へのカーネル長さスケール
  * `xyLS`: （オプション）共変量から結果へのカーネル長さスケール
  * `tyLS`: 治療から結果へのカーネル長さスケール
  * `yNoise`: 結果予測のためのガウスノイズ
  * `yScale`: 結果予測のためのガウススケール
  * `U`: （オプション）潜在的交絡因子
  * `X`: （オプション）共変量
  * `T`: 治療
  * `Y`: 結果
  * `doT`: 治療介入

戻り値:

  * `MeanITE::Vector{Float64}`: `n`個の個別治療効果の平均値
  * `CovITE::Matrix{Float64}`: `n`個の個別治療効果の共分散行列。
