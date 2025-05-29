```julia
time_average(
    sol::HallThruster.Solution
) -> HallThruster.Solution{_A, _B, _C, S} where {_A, _B, _C, S<:(Vector)}
time_average(
    sol::HallThruster.Solution,
    start_frame::Integer
) -> HallThruster.Solution{_A, _B, _C, S} where {_A, _B, _C, S<:(Vector)}

```

Average a `Solution` over time, starting at frame `start_frame`. Return a `Solution` object with a single frame containing the averaged simulation properties
