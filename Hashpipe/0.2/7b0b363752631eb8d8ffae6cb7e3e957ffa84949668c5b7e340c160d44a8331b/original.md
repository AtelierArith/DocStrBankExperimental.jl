```
status_buf_lock_unlock(f::Function, r_status::Ref{status_t})
```

Safely lock and unlock a shared status buffer for updating its values. This must be done so that the status buffer values aren't changed by multiple processes at the same time.

Example:
