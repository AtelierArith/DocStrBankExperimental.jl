```
load_preference(uuid_or_module_or_name, key, default = nothing)
```

`Preferences.toml`ファイルから特定の設定を読み込み、ロードパスの階層を歩きながらキーを浅くマージし、指定されたUUIDを直接の依存関係としてリストするすべての環境から設定を読み込みます。

ほとんどのユーザーは、呼び出し元の`Module`を自動的に決定する`@load_preference`便利マクロを使用すべきです。
