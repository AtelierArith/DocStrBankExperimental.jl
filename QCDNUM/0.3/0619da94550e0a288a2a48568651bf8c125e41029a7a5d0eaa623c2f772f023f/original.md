```
qcdnum_lock()::AbstractLock
```

Get the global lock for QCDNUM operations.

The QCDNUM Fortran package itself is not thread-safe, so QCDNUM.jl uses a global lock do guard against parallel calls to the Fortran library.
