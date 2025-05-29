```
RheoTimeData(;σ::Vector{T1}, ϵ::Vector{T2}, t::Vector{T3}) where {T1<:Real, T2<:Real, T3<:Real}
```

`RheoTimeData` struct contains stress, strain and time data.

If preferred, an instance can be generated manually by just providing the three data vectors in the right order, sampling type will be checked automatically.

# Fields

  * `σ`: stress
  * `ϵ`: strain
  * `t`: time
  * `log`: a log of struct's events, e.g. preprocessing
