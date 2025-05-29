```
FITS_filnam
```

mutable FITS object to hold the decomposed name of a `.fits` file.

The fields are: " `.value`:  for `p#.fits` this is `p#.fits` (`::String`)

  * `.name`:  for `p#.fits` this is `p#` (`::String`)
  * `.prefix`:  for `p#.fits` this is `p` (`::String`)
  * `.numerator`:  for `p#.fits` this is `#`, a serial number (e.g., '3') or a range (e.g., '3-7') (`::String`)
  * `.extension`:  for `p#.fits` this is `.fits` (`::String`)
