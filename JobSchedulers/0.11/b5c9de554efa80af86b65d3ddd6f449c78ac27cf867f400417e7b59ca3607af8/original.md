```
set_scheduler_backup(
    filepath::AbstractString = "";
    migrate::Bool = false,
    delete_old::Bool = false,
    recover_settings::Bool = true,
    recover_queue::Bool = true
)
```

Set the backup file of job scheduler.

If `filepath` was set to `""`, stop backup at exit.

If `filepath` was set to an existing file, `recover_settings` or `recover_queue` from `filepath` immediately.

If `filepath` was set to a new file, the backup file will be created at exit.

If `migrate=true` and the old `JobSchedulers.SCHEDULER_BACKUP_FILE` exists, the old backup file will be recovered before recovering from `filepath`.
