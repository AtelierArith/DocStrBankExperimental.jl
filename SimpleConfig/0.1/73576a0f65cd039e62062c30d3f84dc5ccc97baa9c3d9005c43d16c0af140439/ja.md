```
define_configuration([args,] cfg, defaults::Dict)
define_configuration([args,] cfg, fname::String)
```

`cfg`を使用して作成されたArgParse設定を作成します。初期値/デフォルトは辞書を使用して指定できます（指定方法については`Configurations.from_dict`を参照してください）。もう一つのcfgは、`toml`、`yml`、または`json`タイプの構成ファイルへのパスを渡すためのものです。
