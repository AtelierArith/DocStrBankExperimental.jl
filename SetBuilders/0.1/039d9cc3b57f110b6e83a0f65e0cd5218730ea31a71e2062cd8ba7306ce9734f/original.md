```
describe(set <: SBSet; mark=nothing, collect=nothing) :: String
```

returns a string describing a set

# Example

```julia
julia> I = @setbuild(Integer)
TypeSet(Integer)

julia> P = @setbuild(x in I, 0 <= x < 10)
PredicateSet((x ∈ TypeSet(Integer)) where 0 <= x < 10)

julia> println(describe(P))
{ x ∈ A | 0 <= x < 10 }, where
    A = { x ∈ ::Integer }
```

# Keywords

**`mark`** specifies a set to apply markings to. User also can change the marking letters by assigining a tuple of a set and a mark string.

```julia
julia> println(describe(P, mark=(I, "## ")))
{ x ∈ A | 0 <= x < 10 }, where
 ## A = { x ∈ ::Integer }
```
