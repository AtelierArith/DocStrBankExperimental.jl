```
SequentialBatchAM(::AcquisitionMaximizer, ::Int)
SequentialBatchAM(; am, batch_size)
```

バッチ目的関数評価のための複数の候補を提供します。

以下のステップを繰り返すことで、候補を順次選択します：

  * 1. 'inner' acquisition maximizerを使用して候補`x`を選択します。
  * 2. 候補`x`とサロゲートの事後予測平均`ŷ`を用いて作成された'投機的'な新しいデータポイントでデータセットを拡張します。
  * 3. `batch_size`の候補が選択された場合、それらを返します。

    そうでない場合は、ステップ1に戻ります。

# キーワード

  * `am::AcquisitionMaximizer`: 内部のアクイジションマキシマイザー。
  * `batch_size::Int`: 選択される候補の数。
