```
config_logger(log::LoggerConfig)
config_logger(; args...)
```

グローバルな FloatTracker 設定インスタンスのロガーを設定します。

`LoggerConfig` 構造体、または `LoggerConfig` コンストラクタと同じキーワード引数を取ります。

指定された引数が少数の場合、それらのフィールドのみが上書きされます。つまり、全体の LoggerConfig は置き換えられません。これは、テストの途中でフィールドを調整する必要がある場合などに便利です。
