```
squarefromstring(s::AbstractString)
```

Tries to convert a string to a `Square`.

The return value is of type `Union{Square, Nothing}`.

If the input string is too short, or if the two first characters do not represent a square in standard algebraic notation, returns `nothing`. If the first two characters do represent avalid square, that square is returned, even if there are additional characters.

# Examples

```julia-repl
julia> squarefromstring("d6")
SQ_D6

julia> squarefromstring("xy") == nothing
true

julia> squarefromstring("") == nothing
true

julia> squarefromstring("g1f3")
SQ_G1
```
