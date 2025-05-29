`cancel(cancellable_task, reason = nothing)` ブロッキング/イールドタスクを `CancellationError(reason)` でキャンセルします。タスクは必要に応じて try ... catch ブロックでこのエラーを捕捉することができます。
