```
DebugStoppingCriterion <: DebugAction
```

停止基準によって提供された理由を印刷します。通常、これは空であるべきですが、アルゴリズムが停止した場合はそうではありません。

# フィールド

  * `prefix=""`: 出力を印刷するためのフォーマット
  * `io=stdout`: デバッグを印刷するためのデフォルトストリーム。

# コンストラクタ

DebugStoppingCriterion(prefix = ""; io::IO=stdout)
