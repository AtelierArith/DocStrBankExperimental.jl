```
hushexit(f::Function)
```

Wraps a call to function f in a try/catch:

  * On SIGPIPE:        no error msg; no backtrace; exit code 0   (for broken Unix pipes).
  * On interrupt:      no error msg; no backtrace; exit code 130 (even in script).
  * On `EnduserError`: error msg but no backtrace; exit code is the exception's one.
  * ..rethrows otherwise.
