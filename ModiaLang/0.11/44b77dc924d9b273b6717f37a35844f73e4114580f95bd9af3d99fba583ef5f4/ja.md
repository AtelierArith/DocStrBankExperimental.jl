```
modelInstance = @instantiateModel(model; FloatType = Float64, aliasReduction=true, unitless=false,
    evaluateParameters=false, log=false, logModel=false, logDetails=false, logStateSelection=false,
    logCode=false,logExecution=logExecution, logCalculations=logCalculations, logTiming=false)
```

モデルをインスタンス化します。つまり、構造的および象徴的な変換を行い、シミュレーションに適した導関数の計算のための関数を生成します。

  * `model`: モデル（宣言と方程式）
  * `FloatType`: 浮動小数点数の変数タイプ。例えば: Float64, Measurements{Float64}, StaticParticles{Float64,100}, Particles{Float64,2000}
  * `aliasReduction`: エイリアスの排除を行い、特異点を削除します
  * `unitless`: 単位を削除します（モデルのデバッグ時に便利で、MonteCarloMeasurementsに必要）
  * `evaluateParameters`: 生成されたコードで評価されたパラメータを使用します。
  * `log`: 翻訳の異なるフェーズをログに記録します
  * `logModel`: モデルの変数と方程式をログに記録します
  * `logDetails`: 翻訳の異なるフェーズ中の内部データをログに記録します
  * `logStateSelection`: 状態選択中の詳細をログに記録します
  * `logCode`: 生成されたコードをログに記録します
  * `logExecution`: 生成されたコードの実行をログに記録します（コンパイルのタイミングに便利）
  * `logCalculations`: 生成されたコードの計算をログに記録します（単位バグを見つけるのに便利）
  * `logTiming`: 異なるフェーズのタイミングをログに記録します
  * `return modelInstance prepared for simulation`
