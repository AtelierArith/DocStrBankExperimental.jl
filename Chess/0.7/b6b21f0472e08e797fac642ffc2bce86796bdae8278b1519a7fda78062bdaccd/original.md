```
filefromchar(c::Char)
```

Tries to convert a character to a file.

The return value is a `Union{SquareFile, Nothing}`. The `nothing` is returned in case the character does not represent a valid file.

# Examples

```julia-repl
julia> filefromchar('c')
FILE_C

julia> filefromchar('2') == nothing
true
```
