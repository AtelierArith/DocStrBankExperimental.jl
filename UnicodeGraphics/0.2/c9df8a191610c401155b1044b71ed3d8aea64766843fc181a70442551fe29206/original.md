```
ustring(f, A, [method])
```

Return a string containing a binary unicode representation of `A`, filling values for which `f` returns `true`.

The printing method can be specified by passing either `:braille`, `:block`, `:quadrant`, `:sextant`, or `:octant`. The default is `:braille`. (Note that `:octant` requires either a font or a terminal emulator that supports Unicode 16; otherwise the output will look strange.)

# Example

```julia-repl
julia> A = rand(1:9, 8, 8)
8×8 Matrix{Int64}:
 8  7  9  6  9  8  3  7
 9  9  3  3  5  5  3  2
 1  6  8  3  7  9  3  7
 9  4  4  7  8  7  3  4
 3  8  7  2  2  1  6  6
 4  8  9  4  1  3  4  6
 4  9  6  2  3  4  8  4
 7  2  7  9  8  2  6  7

julia> ustring(iseven, A)
"⢡⡌⡈⢐
⢞⠼⣡⡿
"

julia> ustring(>(3), A, :block)
"██▀▀██ ▀
▄██▄██ █
▄██▄  ██
█▀█▄▄▀██
"
```
