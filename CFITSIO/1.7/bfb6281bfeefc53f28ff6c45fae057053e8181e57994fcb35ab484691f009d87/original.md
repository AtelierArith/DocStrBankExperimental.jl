```
fits_copy_data(fin::FITSFile, fout::FITSFile)
```

Copy the data (not the header) from the current HDU in `fin` to the current HDU in `fout`. This will overwrite pre-existing data in the output HDU.
