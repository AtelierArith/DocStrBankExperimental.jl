```
Config(; debug_mode::Bool=false, silence_debug_messages::Bool=false)
```

`ADTypes.AutoMooncake`で使用するための構成構造体。

# キーワード引数

  * `debug_mode::Bool=false`: 関数を微分する際に追加の型チェックを実行するかどうか。これはかなりの実行時オーバーヘッドがあり、Mooncakeで何か問題が発生している場合にのみオンにするべきです。
  * `silence_debug_messages::Bool=false`: `false`で`debug_mode`が`true`の場合、Mooncakeはデバッグモードが有効であることを示す警告を表示します。これは、デバッグモードを誤ってオンにしたままにしないようにするためです。これらのメッセージを無効にしたい場合は、これを`true`に設定してください。
