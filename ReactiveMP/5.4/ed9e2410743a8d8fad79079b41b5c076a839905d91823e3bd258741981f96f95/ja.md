BIFMMetaオブジェクトの初期化は、次のように呼び出すことで行うことができます。

```julia
meta = BIFMMeta(A, B, C, μu, Σu)
```

ここで、`A`、`B`、および`C`はモデル内の遷移行列です。`μu`と`Σu`は入力の平均ベクトルと共分散行列です。重要なことに、この設定では、これらが既知であり、外部モデルによって変化しないと仮定しています。
