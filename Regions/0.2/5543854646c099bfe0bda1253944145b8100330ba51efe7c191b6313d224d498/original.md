```
translate(r::Run, x::Integer, y::Integer)
translate(r::Run, a::Vector{Int64})
```

Translate a run. Translation moves a run. A run is translated by adding offsets to its row and  columns.

In addition to the translate method, you can also use the + or - operators to translate a run.

```jldoctest reg
julia> using Regions

julia> translate(Run(1, 20:30), 10, 20)
Run(21, 30:40)

julia> translate(Run(1, 2:3), [10, 20])
Run(21, 12:13)

julia> Run(1, 2:3) + [10, 20]
Run(21, 12:13)

julia> [1, 2] + Run(0, 0:10)
Run(2, 1:11)

julia> Run(0, 0:100) - [5, 25]
Run(-25, -5:95)
```
