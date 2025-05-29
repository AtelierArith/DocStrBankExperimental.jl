```
name(C::Card)::String
```

Return the long-form name of the card.

```julia
julia> c = Card(:diamonds, 10)
T♢

julia> name(c)
"ten of diamonds"
```
