```
label(txt::T where T <: AbstractString, direction::Float64, pos::Point=O;
    offset=5,
    leader=false,
    leaderoffsets=[0.0, 1.0])
```

Add a text label at a point, positioned relative to that point, for example, `0.0` is East, `pi` is West.

```julia
label("text", pi)          # positions text to the left of the origin
```
