`read_metadata_from_fits( filename, fields )` Read metadata in FITS header for specified keys and return data as a Dict.  `fields` can be an array of symbols or strings. Optional inputs:

  * Passing both fields (an array of symbols) and fields_str (an array of strings) as named parameters allows for differences in string used in FITS file and Symbol used in resulting Dict.
  * hdu: Specifies which HDU to read from the FITS file.  (Default: 1)
