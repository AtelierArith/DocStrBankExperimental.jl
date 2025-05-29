```
writefile!(edfh, newpath; acquire=dummyacquire, sigformat=same)
```

Write to data in the edfh struct to the file indicated by newpath Returns the file handle of the file written, opened for reading

NOTE: The header needs to be completely specified at function start except for the final number of records, which will be updated after all data records are written. For a system that is recording the data as it is written, the acquire(edfh) function should write the data according the the header parameters. NB: iff the function converts from BDF to EDF or EDF to BDF, the edfh struct is changed.
