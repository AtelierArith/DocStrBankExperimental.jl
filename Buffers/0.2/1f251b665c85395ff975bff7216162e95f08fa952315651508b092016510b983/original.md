```
drop!(buf, tensor...)
```

Drop tensor(s) from buffer `buf`.

Only last tensors can be dropped.   For `ThreadsBuffer`, drop tensors from the buffer of the current thread.
