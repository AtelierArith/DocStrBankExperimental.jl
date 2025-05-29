```
fits_write_chksum(f::FITSFile)
```

Compute and write the `DATASUM` and `CHECKSUM` keyword values for the CHDU into the current header. If the keywords already exist, their values will be updated only if necessary (i.e., if the file has been modified since the original keyword values were computed).
