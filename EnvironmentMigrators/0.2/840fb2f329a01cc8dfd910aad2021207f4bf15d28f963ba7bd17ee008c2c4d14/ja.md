EnvironmentMigrators.jlへようこそ。

`EnvironmentMigrators.wizard()`を使用してインタラクティブに操作します。

# 高レベルインターフェース（未エクスポート）

  * `list_shared_environments([depot])`
  * `select_shared_environments([depot])`
  * `backup_current_environment(; fileaction = cp)`
  * `migrate_selected_environment(selected_environment; backup = true)`
  * `migrate_current_environment_to(path)`
  * `wizard([depot])`

# エクスポートされた型

  * `SimpleEnvironmentMigrator`
  * `SimpleBackupOnlyEnvironmentMigrator`

# エクスポートされたメソッド

  * `migrate(m::EnvironmentMigrators.AbstractEnvironmentMigrator)`
  * `backup(m::EnvironmentMigrators.AbstractEnvironmentMigrator)`
