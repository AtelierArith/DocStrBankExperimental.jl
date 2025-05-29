```
DebugIterate <: DebugAction
```

現在の反復（`get_iterate(o)`に保存されている）をデバッグします。

# コンストラクタ

```
DebugIterate()
```

# パラメータ

  * `io`:        （`stdout`）デフォルトのデバッグ出力ストリーム。
  * `format`:    （`"$prefix %s"`）現在の反復を印刷する方法のフォーマット
  * `long`:      （`false`）長い（`"current iterate:"`）または短い（`"p:"`）プレフィックスを持つかどうか
  * `prefix`     （デフォルトについては`long`を参照）反復の前に印刷されるプレフィックスを設定
