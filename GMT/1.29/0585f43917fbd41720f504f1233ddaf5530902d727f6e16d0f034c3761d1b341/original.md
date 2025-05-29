```
gmtvector(cmd0::String="", arg1=nothing, kwargs...)
```

Time domain filtering of 1-D data tables.

See full GMT (not the `GMT.jl` one) docs at [`gmtvector`](http://docs.generic-mapping-tools.org/latest/gmtvector.html)

## Parameters

  * **A** | **primary_vec** :: [Type => Str]   `Arg = m[conf]|vector`

    Specify a single, primary vector instead of reading tables.
  * **C** | **cartesian** :: [Type => Str | []]        `Arg = [i|o]`

    Select Cartesian coordinates on input and output.
  * **E** | **geod2geoc** :: [Type => Bool]

    Convert input geographic coordinates from geodetic to geocentric and output geographic   coordinates from geocentric to geodetic.
  * **N** | **normalize** :: [Type => Bool]

    Normalize the resultant vectors prior to reporting the output.
  * **S** | **secondary_vec** :: [Type => Str | List]    `Arg = [vector]`

    Specify a single, secondary vector in the same format as the first vector.
  * **T** | **transform** :: [Type => Str | List]     `Arg = a|d|D|paz|s|r[arg|R|x]`

    Specify the vector transformation of interest.
