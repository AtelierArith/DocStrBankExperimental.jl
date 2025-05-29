`conductor(c::Cyc)`

returns the smallest positive integer  n such that `c∈ ℚ (ζₙ)`

`conductor(a::AbstractArray)`

smallest positive integer  n such that all elements of `a` are in `ℚ (ζₙ)`

```julia-repl
julia> conductor(E(6))
3

julia> conductor([E(3),1//2,E(4)])
12
```
