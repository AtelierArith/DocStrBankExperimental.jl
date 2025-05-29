```
Cycles(frequency)
```

Cycles from 0 to 2π to repeat at a `frequency` (with frequency units, like `Hz`). Supports [`make_series`](@ref).

```jldoctest
julia> using AudioSchedules


julia> using Unitful: Hz


julia> first(make_series(Cycles(440Hz), 44100Hz))
0.06268937721449021
```
