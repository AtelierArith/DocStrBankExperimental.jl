```
QuantileRegression
```

分位数回帰の表現

## フィールド

  * `τ`: 分位数値
  * `X`: モデル行列
  * `β`: 回帰係数
  * `y`: 応答ベクトル
  * `wts`: 重み
  * `wrkres`: 作業残差
  * `formula`: `FormulaTerm`オブジェクトまたは`nothing`
  * `fitdispersion`: trueの場合、分散が推定され、そうでない場合は固定される
  * `fitted`: trueの場合、モデルはすでにフィッティングされている
