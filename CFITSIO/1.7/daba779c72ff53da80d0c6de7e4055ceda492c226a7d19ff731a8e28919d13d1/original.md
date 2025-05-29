```
fits_update_chksum(f::FITSFile)
```

Update the `CHECKSUM` keyword value in the CHDU, assuming that the `DATASUM` keyword exists and already has the correct value.
