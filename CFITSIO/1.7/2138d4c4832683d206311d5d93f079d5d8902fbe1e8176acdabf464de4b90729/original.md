```
fits_copy_hdu(fin::FITSFile, fout::FITSFile[, morekeys::Integer = 0])
```

Copy the current HDU from the input file `fin` and append it to the output file `fout`. Space may be reserved for `morekeys` additional keywords in the output header.
