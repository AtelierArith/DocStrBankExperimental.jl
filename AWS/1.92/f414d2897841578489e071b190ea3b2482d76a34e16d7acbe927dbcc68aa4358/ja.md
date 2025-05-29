```
aws_get_profile_settings(profile::AbstractString, ini::Inifile) -> Dict
```

指定されたプロファイルのすべての設定を含む `Dict` を返します。

# 引数

  * `profile::AbstractString`: 設定を取得するプロファイル
  * `ini::Inifile`: 設定を読み取る構成ファイル
