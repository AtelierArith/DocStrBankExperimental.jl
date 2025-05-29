```
backup(m::AbstractEnvironmentMigrator)
```

Backup an environment. Typically, this involves copying the Project.toml and Manifest.toml to a time-stamped backup subfolder.

# Extended Help

The standard backup procedure is as follows.

1. Check that the target project and manifest TOMLs are in the same directory.
2. Check that one of either the project or manifest TOMLs exist
3. Create a time stamp in the format "yyyy-mm-dd*HH*MM_SS
4. Create a subpath in the same directory as the project TOML called `backups/[timestamp]`
5. Copy (or move) the project and manifest TOMLs to the backup path if they exist.
