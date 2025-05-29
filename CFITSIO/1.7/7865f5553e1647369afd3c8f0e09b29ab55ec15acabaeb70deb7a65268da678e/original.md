```
fits_movnam_hdu(f::FITSFile, extname::String, extver::Integer=0,
                hdu_type_int::Integer=-1)
```

Change the current HDU by moving to the (first) HDU which has the specified extension type and EXTNAME and EXTVER keyword values (or HDUNAME and HDUVER keywords).

If `extver` is 0 (the default) then the EXTVER keyword is ignored and the first HDU with a matching EXTNAME (or HDUNAME) keyword will be found. If `hdu_type_int` is -1 (the default) only the extname and extver values will be used to locate the correct extension. If no matching HDU is found in the file, the current HDU will remain unchanged.
