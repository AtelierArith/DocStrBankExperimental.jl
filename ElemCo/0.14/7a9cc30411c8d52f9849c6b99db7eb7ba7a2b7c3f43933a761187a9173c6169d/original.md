```
@write_ints(file="FCIDUMP", tol=-1.0)
```

Write FCIDump integrals to file `file`.

If `tol` is negative, all integrals are written, otherwise only integrals with absolute value larger than `tol` are written.
