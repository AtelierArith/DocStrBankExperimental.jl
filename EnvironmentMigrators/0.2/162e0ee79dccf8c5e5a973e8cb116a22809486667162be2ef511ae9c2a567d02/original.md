```
migrate(m::AbstractEnvironmentMigrator; backup = true, update = true)
```

Move an environment from one place to another. `backup` - whether to perform a backup of the target environment (`true`) or not (`false`). `update` - whether to perform an update of the source environment (`true`) or not (`false`).

# Extended Help

The typical migration procedure is as follows.

1. Backup the target environment by moving the files if indicated.
2. Copy the (Julia)Project.toml from the source to the target environment.
3. Copy the (Julia)Manifest.toml from the source to the target environment.
4. Activate the target environment
5. `Pkg.status()`
6. `Pkg.upgrade_manifest()` - skip if error
7. `Pkg.resolve()`
8. `Pkg.instantiate()`
9. `Pkg.status()`
10. `Pkg.update()`
