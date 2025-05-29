```
dload(sym::Symbol, pids, files=defaultFiles(sym,pids))
```

Import the content of symbol `sym` by each worker specified by `pids` from the corresponding filename in `files`.
