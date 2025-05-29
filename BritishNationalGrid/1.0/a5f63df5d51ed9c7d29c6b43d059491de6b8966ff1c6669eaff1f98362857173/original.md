```
square(p::BNGPoint) -> XX::String
```

Return a two-character string `XX` containing the name of the 100 km-by 100 km square in which is located the point `p`.

```jldoctest
julia> using BritishNationalGrid

julia> BritishNationalGrid.square(BNGPoint(200_000, 1_000_000))
"HX"

```
