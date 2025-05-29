```
tf_config_injector(log::InjectorConfig)
tf_config_injector(; args...)
```

グローバルな TrackedFloats 設定インスタンスのためのインジェクタを設定します。

`InjectorConfig` 構造体、または `InjectorConfig` コンストラクタと同じキーワード引数を取ります。

キーワード引数の部分リストを渡すことは、`tf_config_logger` と同じ動作をします。
