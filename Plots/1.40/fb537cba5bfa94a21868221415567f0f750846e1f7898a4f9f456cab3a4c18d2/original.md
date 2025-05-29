```
yticks(p::Plot)
```

returns a vector of the y-axis ticks of the subplots of `p`.

Example use:

```jldoctest
julia> p = plot(1:5, yticks=[1,2])

julia> yticks(p)
1-element Vector{Tuple{Vector{Float64}, Vector{String}}}:
 ([1.0, 2.0], ["1", "2"])
```

If `p` consists of a single subplot, you might want to grab only the first element, via

```jldoctest
julia> yticks(p)[1]
([1.0, 2.0], ["1", "2"])
```

or you can call yticks on the first (only) subplot of `p` via

```jldoctest
julia> yticks(p[1])
([1.0, 2.0], ["1", "2"])
```
