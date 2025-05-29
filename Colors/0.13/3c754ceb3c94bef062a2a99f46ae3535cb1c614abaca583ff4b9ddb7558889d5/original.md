```
hex(c::Colorant)
hex(c::Colorant, style::Symbol)
```

Convert a color to a hexadecimal string, optionally specifying its style.

# Arguments

  * `c`: a target color.
  * `style`: a symbol to specify the hexadecimal notation. Spesifying the uppercase symbols means the return values are in uppercase. The following symbols are available:

      * `:AUTO`: notation automatically selected according to the type of `c`
      * `:RRGGBB`/`:rrggbb`: 6-digit opaque notation
      * `:AARRGGBB`/`:aarrggbb`: 8-digit notation with alpha at the head
      * `:RRGGBBAA`/`:rrggbbaa`: 8-digit notation with alpha at the tail
      * `:RGB`/`:rgb`/`:ARGB`/`:argb`/`:RGBA`/`:rgba`: 3-digit or 4-digit noatation
      * `:S`/`:s`: short notation if available

# Examples

```jldoctest; setup = :(using Colors)
julia> hex(RGB(1,0.5,0))
"FF8000"

julia> hex(ARGB(1,0.5,0,0.25))
"40FF8000"

julia> hex(HSV(30,1.0,1.0), :AARRGGBB)
"FFFF8000"

julia> hex(ARGB(1,0.533,0,0.267), :rrggbbaa)
"ff880044"

julia> hex(ARGB(1,0.533,0,0.267), :rgba)
"f804"

julia> hex(ARGB(1,0.533,0,0.267), :S)
"4F80"
```

!!! compat "Colors v0.12"
    `style` requires at least Colors v0.12.

