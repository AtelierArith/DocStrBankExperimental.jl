```
COFFRPath
```

COFF RPath object; note that while COFF files do not have an RPath within them, they *do* seach the same directory as the loading binary (e.g. the `$ORIGIN`). We use `COFFRPath` to effect this, although strictly speaking there is no such thing as a "COFF RPath".
