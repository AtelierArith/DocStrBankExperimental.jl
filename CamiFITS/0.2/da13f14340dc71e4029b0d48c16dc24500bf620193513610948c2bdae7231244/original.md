```
FITS_HDU
```

Object to hold a single "Header and Data Unit" (HDU).

The fields are

  * `.hduindex:`:  identifier (a file may contain more than one HDU) (`:Int`)
  * `.header`:  the header object (`::FITS_header`)
  * `.dataobject`:  the data object (`::FITS_dataobject`)

NB. An empty data block (`.dataobject = nothing`) conforms to the standard.
