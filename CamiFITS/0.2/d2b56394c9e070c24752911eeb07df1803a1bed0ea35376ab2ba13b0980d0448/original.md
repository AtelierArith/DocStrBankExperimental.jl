```
FITS_card
```

Object to hold the card information of the [`FITS_header`](@ref) object.

The fields are:

  * `.cardindex`:  identifier of the header record (`::Int`)
  * `.record`:  the full record on the card (`::String`)
  * `.keyword`:  name of the corresponding header record (`::String`)
  * `.val`:  value  of the corresponding header record (`::Any`)
  * `.comment`:  comment on the corresponding header record (`::String`)
