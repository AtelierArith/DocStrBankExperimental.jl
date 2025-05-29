```
fits_write_date(f::FITSFile)
```

Write the current date and time into the FITS header. If a DATE keyword already exists, it is replaced by the new value. The date is written in the format `YYYY-MM-DDThh:mm:ss` (ISO 8601).
