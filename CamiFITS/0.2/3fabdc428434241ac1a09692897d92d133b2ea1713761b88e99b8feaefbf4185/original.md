```
FITS_header
```

Object to hold the header information of a [`FITS_HDU`](@ref).

The fields are:

  * `.card`: the array of `cards` (`::Vector{FITS_card}`)
  * `.map`:  Dictionary `keyword => recordindex` (`::Dict{String, Int}`)
  * `.size`: length in bytes (`::Int`)
