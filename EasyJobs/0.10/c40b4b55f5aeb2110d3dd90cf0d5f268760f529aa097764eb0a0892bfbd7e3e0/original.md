```
queue(table; sortby=:created_at)
```

Return all `Job`s that are pending, running, or finished.

Accpetable arguments for `sortby` are `:created_by`, `:created_at`, `:started_at`, `:stopped_at`, `:spent`, `:status`, and `:n`.
