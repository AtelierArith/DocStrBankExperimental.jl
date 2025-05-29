```
fits_write_null_img(f::FITSFile, firstelem::Integer, nelements::Integer)
```

Set a stretch of elements to the appropriate null value, starting from the pixel number `firstelem` and extending over `nelements` pixels.
