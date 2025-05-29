```
@dit_str -> DitStr64
```

Construct a dit string. such as `dit"0201;3"`. The dit strings also supports string `join`. Just use it like normal strings.

## Example

```jldoctest
julia> dit"10201;3"
10201 ₍₃₎

julia> dit"100_121_121;3"
100121121 ₍₃₎

julia> join(dit"1021;3", dit"11;3", dit"1210;3")
1021111210 ₍₃₎

julia> onehot(dit"1021;3")
81-element Vector{ComplexF64}:
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
     ⋮
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im

```
