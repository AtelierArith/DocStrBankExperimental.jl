```
exe([string, strin,..]; fail=true, onlystdout=stdout, splitlines=true)
```

Wrapper to to run commands and grab rc/stdout/stderr.

Fails with exception on non-zero exit code if `fail==true`.

If `onlystdout==true`, returns either string or vector of strings from stdout, depending on `splitlines`.

If `onlystdout==false`, returns (rc, out, err)- or (rc, outs, errs)-tuple, again depending on split/no split.
