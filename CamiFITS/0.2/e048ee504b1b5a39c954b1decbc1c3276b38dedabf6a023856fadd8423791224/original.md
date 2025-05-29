```
fits_terminology([term::String [; test=false]])
```

Description of the *defined terms* from [FITS standard](https://fits.gsfc.nasa.gov/fits_standard.html): 

ANSI, ASCII, ASCII NULL, ASCII character, ASCII digit, ASCII space, ASCII text,  Array, Array value, Basic FITS, Big endian, Bit, Byte, Card image,  Character string, Conforming extension, Data block, Deprecate, Entry,  Extension, Extension type name, FITS, FITS Support Office, FITS block,  FITS file, FITS structure, Field, File, Floating point, Fraction,  Group parameter value, HDU Header and Data Unit., Header, Header block, Heap,  IAU, IAUFWG, IEEE, IEEE NaN, IEEE special values, Indexed keyword,  Keyword name, Keyword record, MEF, Mandatory keyword, Mantissa, NOST,  Physical value, Pixel, Primary HDU, Primary data array, Primary header,  Random Group, Record, Repeat count, Reserved keyword, SIF, Special records,  Standard extension.

```
julia> fits_terminology()
FITS defined terms:
ANSI, ASCII, ASCII NULL, ASCII character, ..., SIF, Special records, Standard extension.

julia> fits_terminology("FITS")
FITS:
Flexible Image Transport System.

julia> get(dictDefinedTerms, "FITS", nothing)
"Flexible Image Transport System."

julia> fits_terminology("p")
p:
Not one of the FITS defined terms.
suggestions: Physical value, Pixel, Primary HDU, Primary data array, Primary header.

see FITS Standard - https://fits.gsfc.nasa.gov/fits_standard.html
```
