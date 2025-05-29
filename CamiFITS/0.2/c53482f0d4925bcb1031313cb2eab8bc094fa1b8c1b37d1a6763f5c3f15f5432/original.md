```
cast_FORTRAN_format(format::String)
```

Decompose the format specifier `format` into its fields and cast this into the [`FORTRAN_format`](@ref) object. Allowed format specifiers are of the types: `Aw`, `Iw.m`, `Bw.m`, `Ow.m`, `Zw.m`, `Fw.d`, `Ew.dEe`, `ENw.d`, `ESw.d`, `Gw.dEe`, `Dw.dEe`, with: `w` - width, `m`(optional) - minimum number of digits, `d` - number of digits to right of decimal, `e` - number of digits in exponent; `N`/`S` (optional) indicates engineering/scientific formating of the `E` type.

#### Examples:

```
julia> cast_FORTRAN_format("I10")
FORTRAN_format("Iw", 'I', nothing, 10, 0, 0, 0)

julia> cast_FORTRAN_format("I10.12")
FORTRAN_format("Iw.m", 'I', nothing, 10, 12, 0, 0)

julia> F = cast_FORTRAN_format("E10.5E3")
FORTRAN_format("Ew.dEe", 'E', nothing, 10, 0, 5, 3)

julia> F.Type, F.TypeChar, F.EngSci, F.width, F.nmin, F.ndec, F.nexp
("Ew.dEe", 'E', nothing, 10, 0, 5, 3)  
```
