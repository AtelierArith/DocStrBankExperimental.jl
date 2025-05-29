```
DebugIterate <: DebugAction
```

現在の反復（`get_iterate(o)`に格納されている）をデバッグします。

# コンストラクタ

```
DebugIterate(; kwargs...)
```

# キーワード引数

  * `io=stdout`:           デバッグを出力するデフォルトストリーム。
  * `format="$prefix %s"`: 現在の反復を印刷する方法のフォーマット
  * `long=false`:          長い（`"current iterate:"`）または短い（`"p:"`）プレフィックスのデフォルト
  * `prefix`:              （デフォルトについては`long`を参照）反復の前に印刷されるプレフィックスを設定
