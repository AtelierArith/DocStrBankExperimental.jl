```
ismember(elem, set <: SBSet; on_member::Function, on_nomember::Function)
```

returns `true` if `elem` is a member of `set`. Otherwise returns false.

# Keywords

## `on_member`

A callback function registered with `on_member`  will be called when `elem` is known to be a member of `set`.

## `on_nomember`

A callback function registered with `on_nomember`  will be called when `elem` is known not to be a member of `set`.

```julia
julia> I = @setbuild(Integer)
TypeSet(Integer)

julia> P = @setbuild(x in I, 0 <= x < 10)
PredicateSet((x ∈ TypeSet(Integer)) where 0 <= x < 10)

julia> F = h -> println(describe(h[1].set, mark=h[end].set))
#7 (generic function with 1 method)

julia> ismember(-1, P, on_nomember=F)
=> { x ∈ A | 0 <= x < 10 }, where
    A = { x ∈ ::Integer }
false
```
