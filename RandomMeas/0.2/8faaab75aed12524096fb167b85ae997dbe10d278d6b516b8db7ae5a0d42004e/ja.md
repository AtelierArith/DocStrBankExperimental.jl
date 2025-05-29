```
multiply(shadow1::FactorizedShadow, shadow2::FactorizedShadow)
```

2つの`FactorizedShadow`オブジェクトを要素ごとに乗算します。

# 引数

  * `shadow1::FactorizedShadow`: 最初の`FactorizedShadow`オブジェクト。
  * `shadow2::FactorizedShadow`: 2番目の`FactorizedShadow`オブジェクト。

# 戻り値

2つの入力の要素ごとの積を表す新しい`FactorizedShadow`オブジェクト。

# 注意事項

  * `shadow1`と`shadow2`は同じ数のキュービット/サイトを持っている必要があります。
