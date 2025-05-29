```
isless(x::Run, y::Run)
```

Compare two runs according to their natural sort order. First, their rows are compared, and if they are equal, their column ranges are compared.

```jldoctest reg
julia> using Regions

julia> isless(Run(0, 1:10), Run(1, 0:10))
true

julia> isless(Run(1, 1:10), Run(1, 2:10))
true
```
