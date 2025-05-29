```
adjacentfilesquares(f::SquareFile)
adjacentfilesquares(s::Square)
```

The set of all squares on files adjacent to the input file.

# Examples

```julia-repl
julia> adjacentfilesquares(FILE_F)
SquareSet:
 -  -  -  -  #  -  #  -
 -  -  -  -  #  -  #  -
 -  -  -  -  #  -  #  -
 -  -  -  -  #  -  #  -
 -  -  -  -  #  -  #  -
 -  -  -  -  #  -  #  -
 -  -  -  -  #  -  #  -
 -  -  -  -  #  -  #  -

julia> adjacentfilesquares(FILE_A)
SquareSet:
 -  #  -  -  -  -  -  -
 -  #  -  -  -  -  -  -
 -  #  -  -  -  -  -  -
 -  #  -  -  -  -  -  -
 -  #  -  -  -  -  -  -
 -  #  -  -  -  -  -  -
 -  #  -  -  -  -  -  -
 -  #  -  -  -  -  -  -

julia> adjacentfilesquares(SQ_D4)
SquareSet:
 -  -  #  -  #  -  -  -
 -  -  #  -  #  -  -  -
 -  -  #  -  #  -  -  -
 -  -  #  -  #  -  -  -
 -  -  #  -  #  -  -  -
 -  -  #  -  #  -  -  -
 -  -  #  -  #  -  -  -
 -  -  #  -  #  -  -  -
```
