```
adstring(ra::Real, dec::Real[, precision::Int=2, truncate::Bool=true]) -> string
adstring([ra, dec]) -> string
adstring(dec) -> string
adstring([ra], [dec]) -> ["string1", "string2", ...]
```

### Purpose

Returns right ascension and declination as string(s) in sexagesimal format.

### Explanation

Takes right ascension and declination expressed in decimal format, converts them to sexagesimal and return a formatted string.  The precision of right ascension and declination can be specified.

### Arguments

Arguments of this function are:

  * `ra`: right ascension in decimal degrees.  It is converted to hours before printing.
  * `dec`: declination in decimal degrees.

The function can be called in different ways:

  * Two numeric arguments: first is `ra`, the second is `dec`.
  * An iterable (array, tuple) of two elements: `(ra, dec)`.
  * One numeric argument: it is assumed only `dec` is provided.

Optional keywords affecting the output format are always available:

  * `precision` (optional integer keyword): specifies the number of digits of declination seconds.  The number of digits for right ascension seconds is always assumed to be one more `precision`.  If the function is called with only `dec` as input, `precision` default to 1, in any other case defaults to 0.
  * `truncate` (optional boolean keyword): if true, then the last displayed digit in the output is truncated in precision rather than rounded.  This option is useful if `adstring` is used to form an official IAU name (see http://vizier.u-strasbg.fr/Dic/iau-spec.htx) with coordinate specification.

### Output

The function returns one string.  The format of strings can be specified with `precision` and `truncate` keywords, see above.

### Example

```jldoctest
julia> using AstroLib

julia> adstring(30.4, -1.23, truncate=true)
" 02 01 35.9  -01 13 48"

julia> adstring.([30.4, -15.63], [-1.23, 48.41], precision=1)
2-element Vector{String}:
 " 02 01 36.00  -01 13 48.0"
 " 22 57 28.80  +48 24 36.0"
```
