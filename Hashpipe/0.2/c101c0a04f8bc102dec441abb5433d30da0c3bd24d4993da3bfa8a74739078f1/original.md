```
status_unlock(p_status::Ref{status_t})
```

Unlock the status pointed to by p_status (probably after updating status values).

If unlocked, will sleep while waiting for the buffer to become locked.
