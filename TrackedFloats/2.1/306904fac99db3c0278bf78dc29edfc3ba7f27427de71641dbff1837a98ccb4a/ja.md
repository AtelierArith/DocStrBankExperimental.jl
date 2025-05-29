```
tf_config_session(log::SessionConfig)
tf_config_session(; args...)
```

グローバルな TrackedFloats 設定インスタンスのセッションを設定します。

`SessionConfig` 構造体、または `SessionConfig` コンストラクタと同じキーワード引数を取ります。

キーワード引数の部分リストを渡すことは、`tf_config_logger` と同じ動作をします。
