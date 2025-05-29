`gen_time_domain(fs::Integer, s::Union{Integer, AbstractFloat}, e::Union{Integer, AbstractFloat})`

Generates a vector of Time objects representing the time instances $t_1, \ldots, t_n$ in a signal with with a given sampling rate $f_s$ from second $s$ to second $e$. For instance, $f_s = 500$, $s = 10, e = 11$ would map to $10.002, 10.004, \ldots, 10.998, 11$.

```julia
julia> gen_time_domain(500, 10, 11)
500-element Vector{Time}:
00:00:10.002
00:00:10.004
00:00:10.006
00:00:10.008
00:00:10.01
00:00:10.012
⋮
00:00:10.992
00:00:10.994
00:00:10.996
00:00:10.998
00:00:11

julia> gen_time_domain(500, 600, 6000)
2700000-element Vector{Time}:
00:10:00.002
00:10:00.004
⋮
01:39:59.998
01:40:00
```
