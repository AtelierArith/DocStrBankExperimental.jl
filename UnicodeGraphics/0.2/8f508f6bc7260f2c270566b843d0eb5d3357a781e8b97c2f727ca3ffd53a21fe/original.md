```
ustring(A, [method])
```

Return a string containing a binary unicode representation of `A` , filling values that are `true` or greater than zero.

The printing method can be specified by passing either `:braille`, `:block`, `:quadrant`, `:sextant`, or `:octant`. The default is `:braille`. (Note that `:octant` requires either a font or a terminal emulator that supports Unicode 16; otherwise the output will look strange.)

# Example

```julia-repl
julia> A = rand(Bool, 8, 8)
8×8 Matrix{Bool}:
 1  1  1  1  0  1  0  0
 1  0  0  1  1  1  0  0
 1  0  0  0  1  0  1  0
 1  0  1  0  1  1  1  1
 0  0  0  0  0  0  1  0
 0  1  1  0  1  0  0  1
 0  0  1  0  0  1  1  1
 1  1  1  1  0  0  1  1

julia> ustring(A)
"⡏⡙⣞⣄
⣐⣆⠢⣵
"

julia> ustring(A, :block)
"█▀▀█▄█  
█ ▄ █▄█▄
 ▄▄ ▄ ▀▄
▄▄█▄ ▀██
"
```
