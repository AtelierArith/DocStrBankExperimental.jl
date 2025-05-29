```
FORTRAN_format
```

Object to hold a FORTRAN format specifier decomposed in its fields.

Accepted *datatype specifiers* are:  `Aw`,  `Iw`,  `Fw.d`,  `Ew.d`,  `Dw.d`

Accepted *output formating specifiers* are: `Aw`,  `Iw.m`,  `Bw.m`,  `Ow.m`, `Zw.m`,  `Fw.d`,  `Ew.dEe`,  `ENw.d`,  `ESw.d`,  `Gw.dEe`,  `Dw.dEe`. Notation: `w` - width, `m` (optional) - minimum number of digits, `d` - number of digits to right of decimal, `e` - number of digits in exponent `N`/`S` (optional) indicates engineering/scientific formating of the `E` type.

The fields are:

  * `.datatype`: primary FORTRAN datatype (`::String`)
  * `.char`: primary FORTRAN datatype character (`::Char`)
  * `.EngSci`: secundary datatype character - N for engineering/ S for scientific (`::Union{Char,Nothing}`)
  * `.width`: width of numeric field (`::Int`)
  * `.nmin`: minimum number of digits displayed (`::Int`)
  * `.ndec`: number of digits to right of decimal (`::Int`)
  * `.nexp`: number of digits in exponent (`::Int`)
