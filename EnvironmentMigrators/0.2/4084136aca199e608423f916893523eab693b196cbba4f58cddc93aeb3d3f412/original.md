```
SimpleBackupOnlyEnvironmentMigrator{F}([target_project_toml, target_manifest_toml], fileaction::F)
```

`AbstractEnvironmentMigrator` only for backing up the target project and manifest tomls to a timestamped folder. The target project and manifest tomls will default to the current project and manifest tomls.
