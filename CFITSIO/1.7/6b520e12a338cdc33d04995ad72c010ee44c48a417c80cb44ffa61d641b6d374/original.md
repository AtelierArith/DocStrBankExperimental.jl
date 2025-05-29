```
fits_movrel_hdu(f::FITSFile, hduNum::Integer)
```

Change the current HDU by moving forward or backward by `hduNum` HDUs (positive means forward), and return the same as [`fits_movabs_hdu`](@ref).
