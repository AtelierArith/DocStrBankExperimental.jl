```
JLMatch(;kw...)
```

キーワード引数から `JLMatch` オブジェクトを作成します。

# Kwargs

  * `item`: 一致させるアイテム
  * `map`: パターン=>結果のマップで、`OrderedDict` である必要があります。
  * `fallthrough`: フォールスルーパターン `_` の結果。
  * `mod`: 式を評価するモジュール。
  * `line`: 行番号 `LineNumberNode`。
