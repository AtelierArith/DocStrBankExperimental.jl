```
StatsBase.mad!(x; center=median!(x), normalize=true)
```

配列 `x` の中央値（デフォルトでは中央値の周り）に対する中央値絶対偏差（MAD）を計算し、その過程で `x` を上書きします。`x` は、その要素に対して `middle` を呼び出すことで生成される値を保持できる必要があります（例えば、整数ベクトルは適切ではありません。なぜなら `middle` は非整数値を生成する可能性があるからです）。

`normalize` が `true` に設定されている場合、MAD は `1 / quantile(Normal(), 3/4) ≈ 1.4826` で乗算され、データが正規分布しているという仮定の下で標準偏差の一貫した推定量を得ることができます。
