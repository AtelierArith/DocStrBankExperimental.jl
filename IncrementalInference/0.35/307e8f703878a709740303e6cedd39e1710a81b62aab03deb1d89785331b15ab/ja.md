```julia
calcFactorResidual(dfgfct, args; ccw)

```

ファクター残差関数を評価するためのヘルパー関数で、必要な `CalcFactor` ラッパーを追加します。

ノート

  * ファクターは機能するためにすでにファクターグラフに存在している必要があります
  * すべてのマルチヒポのニュアンスをまだ適切にサポートしていません。テスト用の関数です
  * ファクターのデバッグに役立ちます。

例

```julia
fg = generateGraph_Kaess()

residual = calcFactorResidual(fg, :x1x2f1, [1.0], [0.0], [0.0])
```

関連

[`calcFactorResidualTemporary`](@ref), [`_evalFactorTemporary!`](@ref), [`approxConvBelief`](@ref)
