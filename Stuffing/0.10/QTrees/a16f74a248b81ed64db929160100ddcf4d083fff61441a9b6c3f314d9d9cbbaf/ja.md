```jldoctest
julia> using Plots

julia> ground = [0, 0, 0]
3-element Vector{Int64}:
 0
 0
 0

julia> sortedtrees = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]

julia> for (i, tree) in enumerate(sortedtrees)
           shift = (i - 1) * 10
           ground .+= tree .+ shift
       end

julia> ground
3-element Vector{Int64}:
  1
  2
  3
```
