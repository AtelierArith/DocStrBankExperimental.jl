```
merge_toml_files(filepaths; override)
```

指定されたすべてのTOMLファイルパスを解析してマージし、それらをDictとして返します。これにより、複数のTOMLファイルからtoml_dictを構築することができます。デフォルトでは、非一意のTOMLエントリは許可されていませんが、`override = true`を設定することでこれを変更できます。
