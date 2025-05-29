```
SimpleBackupOnlyEnvironmentMigrator{F}([target_project_toml, target_manifest_toml], fileaction::F)
```

`AbstractEnvironmentMigrator` は、ターゲットプロジェクトとマニフェストの toml をタイムスタンプ付きのフォルダーにバックアップするためだけのものです。ターゲットプロジェクトとマニフェストの toml は、現在のプロジェクトとマニフェストの toml にデフォルト設定されます。
