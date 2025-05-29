Welcome to EnvironmentMigrators.jl.

Use `EnvironmentMigrators.wizard()` for interactive use.

# High level interface (unexported)

  * `list_shared_environments([depot])`
  * `select_shared_environments([depot])`
  * `backup_current_environment(; fileaction = cp)`
  * `migrate_selected_environment(selected_environment; backup = true)`
  * `migrate_current_environment_to(path)`
  * `wizard([depot])`

# Exported types

  * `SimpleEnvironmentMigrator`
  * `SimpleBackupOnlyEnvironmentMigrator`

# Exported methods

  * `migrate(m::EnvironmentMigrators.AbstractEnvironmentMigrator)`
  * `backup(m::EnvironmentMigrators.AbstractEnvironmentMigrator)`
