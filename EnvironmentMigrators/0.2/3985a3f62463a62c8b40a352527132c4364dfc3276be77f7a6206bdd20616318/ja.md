```
SimpleEnvironmentMigrator([source_project_toml, source_target_toml], [target_project_toml, target_manifest_toml])
```

`AbstractEnvironmentMigrator` で、ソースおよびターゲットのプロジェクトとマニフェストファイルをフィールドとして設定できます。`source_project_toml` と `source_manifest_toml` が指定されていない場合、それらは `nothing` になります。`target_project_toml` と `target_manifest_toml` が指定されていない場合、それらは現在の環境に設定されます。

# フィールド

  * `source_project_toml`
  * `source_manifest_toml`
  * `target_project_toml`
  * `target_manifest_toml`

# メソッドの詳細

`fileaction(m)` は、`source_project_toml` が `nothing` の場合は `cp` を返し、それ以外の場合は `mv` を返します。
