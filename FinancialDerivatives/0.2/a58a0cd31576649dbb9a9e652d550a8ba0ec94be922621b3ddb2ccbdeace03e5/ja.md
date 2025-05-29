```
evaluate(O, JarrowRudd(), risk_neutral = true, N = 1000)
```

オプション `O` を `JarrowRudd` 二項モデルを使用して評価します（リスク中立バージョンがデフォルトです）。

# 引数

  * `O::Option`: オプション
  * `risk_neutral`: リスク中立の場合は `true`、等確率の場合は `false`。
  * `N`: シミュレーションするパスの数
