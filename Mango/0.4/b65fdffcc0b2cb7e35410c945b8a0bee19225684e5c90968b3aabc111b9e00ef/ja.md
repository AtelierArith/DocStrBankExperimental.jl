```
stop_task(scheduler::AbstractScheduler, t::Task)
```

`scheduler`によって管理されているタスク`t`を停止します。これは、タスクが停止可能なTaskDataを使用してスケジューラでスケジュールされている場合にのみ機能します。
