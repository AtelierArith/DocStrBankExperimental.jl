```
multiply(shadow1::DenseShadow, shadow2::DenseShadow)
```

2つの密なシャドウのトレース積を計算します。

# 引数

  * `shadow1::DenseShadow`: 最初の密なシャドウ。
  * `shadow2::DenseShadow`: 2番目の密なシャドウ。

# 戻り値

2つの入力シャドウのトレース積を表す新しい `DenseShadow` オブジェクト。

# 注意事項

  * シャドウは同じサイトインデックス (`ξ`) と量子ビットの数 (`N`) を持っている必要があります。
