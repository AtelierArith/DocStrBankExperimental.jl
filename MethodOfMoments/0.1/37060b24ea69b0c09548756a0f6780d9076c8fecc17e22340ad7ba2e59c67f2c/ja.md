```
fit!(m::NonlinearGMM{<:IteratedGMM}; kwargs...)
fit!(m::LinearGMM{<:IteratedLinearGMM}; kwargs...)
```

反復を進めるための[`fit`](@ref)のインプレースバージョンです。
