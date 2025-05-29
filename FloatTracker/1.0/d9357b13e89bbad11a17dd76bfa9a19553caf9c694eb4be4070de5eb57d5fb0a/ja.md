```
config_injector(log::InjectorConfig)
config_injector(; args...)
```

グローバルな FloatTracker 設定インスタンスのためのインジェクタを設定します。

`InjectorConfig` 構造体、または `InjectorConfig` コンストラクタと同じキーワード引数を取ります。

キーワード引数の部分リストを渡すことは、`config_logger` と同じ動作をします。
