```
MK_statistics(T0::Vector, Tk::Vector)
```

正規ノックオフ統計量 tau と W を計算します。

# 入力

  * `T0`: 元の変数の重要度スコアの p ベクトル
  * `Tk`: ノックオフ変数の重要度スコアの p ベクトル

# 出力

  * `W`: コエフィシエント差統計量 `W[i] = abs(T0[i]) - abs(Tk[i])`
