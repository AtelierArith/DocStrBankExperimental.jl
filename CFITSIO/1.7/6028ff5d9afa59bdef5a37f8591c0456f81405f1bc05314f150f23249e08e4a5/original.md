```
fits_read_keyn(f::FITSFile, keynum::Int) -> (name, value, comment)
```

Return the nth header record in the CHU. The first keyword in the header is at `keynum = 1`.
