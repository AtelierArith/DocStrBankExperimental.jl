```
fits_read_record(f::FITSFile, keynum::Int)::String
```

Return the nth header record in the CHU. The first keyword in the header is at `keynum = 1`.
