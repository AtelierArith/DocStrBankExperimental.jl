```
set_scheduler_backup(
    filepath::AbstractString = "";
    migrate::Bool = false,
    delete_old::Bool = false,
    recover_settings::Bool = true,
    recover_queue::Bool = true
)
```

ジョブスケジューラのバックアップファイルを設定します。

`filepath` が `""` に設定されている場合、終了時にバックアップを停止します。

`filepath` が既存のファイルに設定されている場合、`filepath` から `recover_settings` または `recover_queue` を即座に復元します。

`filepath` が新しいファイルに設定されている場合、終了時にバックアップファイルが作成されます。

`migrate=true` で古い `JobSchedulers.SCHEDULER_BACKUP_FILE` が存在する場合、`filepath` から復元する前に古いバックアップファイルが復元されます。
