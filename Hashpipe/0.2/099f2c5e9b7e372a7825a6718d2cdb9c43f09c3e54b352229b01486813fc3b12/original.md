```
status_lock(p_status::Ref{status_t})
```

Lock the status pointed to by p_status (probably for updating status values).

If locked, will sleep while waiting for the buffer to become unlocked.
