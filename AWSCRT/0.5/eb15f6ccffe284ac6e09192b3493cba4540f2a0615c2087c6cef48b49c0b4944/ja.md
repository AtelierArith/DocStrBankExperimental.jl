```
on_connection_interrupted(
    connection::MQTTConnection,
    error_code::Int,
)
```

MQTT接続が失われるたびに呼び出されるコールバック。MQTTクライアントは自動的に再接続を試みます。

引数:

  * `connection (MQTTConnection)`: 接続。
  * `error_code (Int)`: 接続喪失の原因となったエラー。

!!! note
    すべてのコールバックは同時に実行されます。コールバックの実装はスレッドセーフである必要があります。並行性の制限はありません。

