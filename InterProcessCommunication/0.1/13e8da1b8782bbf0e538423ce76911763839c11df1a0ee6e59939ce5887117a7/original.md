```julia
now(T)
```

yields the current time since the Epoch as an instance of type `T`, which can be [`TimeVal`](@ref) or [`TimeSpec`](@ref).

See also: [`gettimeofday`](@ref),  [`time`](@ref),  [`clock_gettime`](@ref).
