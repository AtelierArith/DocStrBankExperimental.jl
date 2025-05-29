```
on_message(connection::MQTTConnection, callback::Union{OnMessage,Nothing})
```

ANYメッセージが受信されたときに呼び出されるコールバックを設定します。

引数:

  * `connection (MQTTConnection)`: 使用する接続。
  * `callback (Union{OnMessage,Nothing})`: メッセージ受信時に呼び出されるオプションのコールバック。必要なシグネチャについては[`OnMessage`](@ref)を参照してください。このコールバックをクリアするには`nothing`に設定します。

何も返しません。

!!! note
    すべてのコールバックは同時に実行されます。コールバックの実装はスレッドセーフである必要があります。並行性の制限はありません。

