```
dstore(sym::Symbol, pids, files=defaultFiles(sym,pids))
```

Export the content of symbol `sym` by each worker specified by `pids` to a corresponding filename in `files`.
