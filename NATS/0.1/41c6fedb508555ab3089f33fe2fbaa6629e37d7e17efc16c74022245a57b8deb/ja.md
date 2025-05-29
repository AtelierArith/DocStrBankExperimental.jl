```julia
next(T, connection, sub; no_wait, no_throw)

```

同期購読のための次のメッセージを取得し、要求された `T` 型に変換します。

オプションのキーワード引数:

  * `no_wait`: 次のメッセージを待たず、バッファが空の場合は `nothing` を返します
  * `no_throw`: 例外をスローせず、次のメッセージを取得できない場合は `nothing` を返します
