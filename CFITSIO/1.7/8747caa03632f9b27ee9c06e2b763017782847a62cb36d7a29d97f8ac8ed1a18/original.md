```
fits_verify_chksum(f::FITSFile)
```

Verify if the checksum of the data and the HDU matches the stored values. Returns a tuple of `CFITSIO.ChecksumVerificationStatus` values, indicating the status of the data and HDU checksums. For either value, a status of `MISSING` indicates that the corresponding keyword is not present, while a status of `MISMATCH` indicates that the keyword is present but the value is incorrect. Finally, a value of `VERIFIED` indicates that the checksum was validated successfully.
