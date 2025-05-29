`cancel(cancellable_task, reason = nothing)` Cancel a blocking/yielding task with a `CancellationError(reason)`. The task may intercept this error in a try ... catch block if necessary.
