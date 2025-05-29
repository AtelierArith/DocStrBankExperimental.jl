```
translate(x::UnitRange{Int64}, y::Integer)
```

Translate a range. Translation moves a range. A range is translated by adding  an offset to each of its coordinates.

In addition to the translate method, you can also use the + or - operators to translate a range.

```jldoctest
julia> using Regions

julia> translate(0:10, 5)
5:15

julia> (5:15) + 10
15:25

julia> 10 + (5:15)
15:25

julia> (5:15) - 10
-5:5
```
