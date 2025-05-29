```
fits_write_key_unit(f::FITSFile, keyname::String, unit::String)
```

Write the physical units string into an existing keyword record. The keyword must already exist in the header. The unit string is enclosed in square brackets at the beginning of the keyword comment field.
