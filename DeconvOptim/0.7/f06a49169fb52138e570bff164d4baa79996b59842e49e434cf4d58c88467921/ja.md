```
invert(measured, rec0, forward; <keyword arguments>)
```

`forward` モデルを反転しようとします。`forward` は `rec0` の形状を持つ入力を受け取り、`measured` と同じ形状のオブジェクトを返す関数です。

異なる損失関数、正則化子、およびマッピングのために複数のキーワード引数を指定できます。

# 引数

  * `loss=Poisson()`: `measured` と比較するために互換性のある損失関数。
  * `regularizer=nothing`: 損失と同じ形式の正則化関数。
  * `λ=0.05`: グローバル損失関数に対する正則化子の総重みを示す浮動小数点数。
  * `mapping=Non_negative()`: 最適化の重みのマッピングを適用します。デフォルトは非負制約を達成する放物線です。
  * `iterations=nothing`: 最適化後に停止すべき反復回数を指定します。`opt_options` が提供される場合は上書きされます。デフォルト: 20
  * `opt_package=Opt_Optim`: 使用する最適化のバックエンドを決定します。
  * `opt=LBFGS()`: `opt_package` に適合する選択された最適化器。
  * `opt_options=nothing`: Optim.jl に必要なオプションファイルである可能性があります。反復を上書きします。
  * `debug_f=nothing`: 現在の再構成を引数として受け取る必要があるデバッグ関数。
