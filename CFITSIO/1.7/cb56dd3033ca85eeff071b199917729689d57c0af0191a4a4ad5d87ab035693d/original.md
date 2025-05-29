```
fits_copy_header(fin::FITSFile, fout::FITSFile)
```

Copy the header (not the data) associated with the current HDU from `fin` to `fout`. If the current HDU in `fout` is not empty, it will be closed and a new HDU will be appended. An empty output HDU will be created with the header but no data.
