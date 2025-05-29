```
isempty(x::Run)
```

Discover whether the run is empty.

```jldoctest
julia> using Regions

julia> isempty(Run(1, 1:10))
false

julia> isempty(Run(2, 1:1))
false

julia> isempty(Run(3, 1:0))
true
```
