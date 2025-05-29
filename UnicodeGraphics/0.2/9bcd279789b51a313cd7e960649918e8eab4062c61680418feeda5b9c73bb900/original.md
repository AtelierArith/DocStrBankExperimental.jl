```
uprint([io::IO], f, A, [method])
```

Write to `io` (or to the default output stream `stdout` if `io` is not given) a binary unicode representation of `A` , filling values for which `f` returns `true`.

The printing method can be specified by passing either `:braille`, `:block`, `:quadrant`, `:sextant`, or `:octant`. The default is `:braille`. (Note that `:octant` requires either a font or a terminal emulator that supports Unicode 16; otherwise the output will look strange.)

# Example

```julia-repl
julia> A = rand(1:9, 8, 8)
8×8 Matrix{Int64}:
 9  1  6  3  4  2  9  6
 4  1  2  8  2  5  9  1
 7  5  6  1  1  4  8  8
 4  8  3  4  8  7  8  8
 4  2  2  6  2  6  1  7
 9  1  4  1  8  1  6  1
 3  8  4  3  9  5  5  6
 1  4  4  2  8  6  3  9

julia> uprint(iseven, A)
⣂⢗⡫⣬
⢩⣏⣋⠢
julia> uprint(>(3), A, :block)
█ ▀▄▀▄█▀
██▀▄▄███
█ ▄▀▄▀▄▀
 ██ ██▀█
```
