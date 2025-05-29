```
@atoms(ps...)
```

Instantiate a collection of [`Atom`](@ref)s and return them as a vector.

!!! info
    Atoms instantiated with this macro are defined in the global scope as constants.


# Examples

```julia-repl
julia> SoleLogics.@atoms String p q r s
4-element Vector{Atom{String}}:
 Atom{String}("p")
 Atom{String}("q")
 Atom{String}("r")
 Atom{String}("s")

julia> p
Atom{String}("p")
```
