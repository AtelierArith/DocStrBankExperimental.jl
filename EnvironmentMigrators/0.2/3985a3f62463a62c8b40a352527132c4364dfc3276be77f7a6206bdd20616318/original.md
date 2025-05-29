```
SimpleEnvironmentMigrator([source_project_toml, source_target_toml], [target_project_toml, target_manifest_toml])
```

An `AbstractEnvironmentMigrator` where one can set source and target project and manifest files as fields. If `source_project_toml` and `source_manifest_toml` are not specified, they will be `nothing`. If `target_project_toml` and `target_manifest_toml` are not specified, they will be set to the current environment.

# Fields

  * `source_project_toml`
  * `source_manifest_toml`
  * `target_project_toml`
  * `target_manifest_toml`

# Method details

`fileaction(m)` will return `cp` if `source_project_toml` is `nothing` or `mv` otherwise.
