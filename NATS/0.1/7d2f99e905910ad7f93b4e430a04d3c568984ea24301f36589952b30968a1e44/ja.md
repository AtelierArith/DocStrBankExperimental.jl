```julia
next(connection, sub; no_wait, no_throw)

```

同期サブスクリプションの次のメッセージを取得します。

オプションのキーワード引数：

  * `no_wait`: 次のメッセージを待たず、バッファが空の場合は `nothing` を返します
  * `no_throw`: 例外をスローせず、次のメッセージを取得できない場合は `nothing` を返します
