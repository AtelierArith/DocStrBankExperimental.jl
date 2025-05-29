```
ClosedFormEntropyZeroGradient()
```

エントロピーの閉形式表現を使用しますが、ADグラフから切り離します。これは`ProximalLocationScaleEntropy`とのみ使用されることが期待されています。

# 要件

  * 変分近似は`entropy`を実装しています。
