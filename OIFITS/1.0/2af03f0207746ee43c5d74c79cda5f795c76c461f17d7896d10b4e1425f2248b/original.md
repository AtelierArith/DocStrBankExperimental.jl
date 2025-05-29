```
OITargetEntry([def::OITargetEntry]; kwds...)
```

yields an entry of the `OI_TARGET` table in an OI-FITS file. All fields are specified by keywords. If template entry `def` is specified, keywords have default values taken from `def`; otherwise all keywords are mandatory but `category` which is assumed to be `""` if unspecified.
