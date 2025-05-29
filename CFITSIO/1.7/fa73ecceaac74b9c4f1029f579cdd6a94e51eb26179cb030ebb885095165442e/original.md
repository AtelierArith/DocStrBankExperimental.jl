```
fits_copy_image_section(fin::FITSFile, fout::FITSFile, section::String)
```

Copy a rectangular section of an image from `fin` and write it to a new FITS primary image or image extension in `fout`. The section specifier is described on the [`CFITSIO website`](https://heasarc.gsfc.nasa.gov/docs/software/fitsio/c/c_user/node97.html).
