```julia
time_average(
    sol::HallThruster.Solution,
    start_time
) -> HallThruster.Solution{_A, _B, _C, S} where {_A, _B, _C, S<:(Vector)}

```

Average a `Solution` over time, starting at time `start_time`. Return a `Solution` object with a single frame containing the averaged simulation properties
