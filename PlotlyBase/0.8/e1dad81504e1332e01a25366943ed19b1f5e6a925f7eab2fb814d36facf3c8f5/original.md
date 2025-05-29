```
extendtraces!(::Plot, ::Dict{Union{Symbol,AbstractString},AbstractVector{Vector{Any}}}), indices, maxpoints)
```

Extend one or more traces with more data. A few notes about the structure of the update dict are important to remember:

  * The keys of the dict should be of type `Symbol` or `AbstractString` specifying the trace attribute to be updated. These attributes must already exist in the trace
  * The values of the dict *must be* a `Vector` of `Vector` of data. The outer index tells Plotly which trace to update, whereas the `Vector` at that index contains the value to be appended to the trace attribute.

These concepts are best understood by example:

```julia
# adds the values [1, 3] to the end of the first trace's y attribute and doesn't
# remove any points
extendtraces!(p, Dict(:y=>Vector[[1, 3]]), [1], -1)
extendtraces!(p, Dict(:y=>Vector[[1, 3]]))  # equivalent to above
```

```julia
# adds the values [1, 3] to the end of the third trace's marker.size attribute
# and [5,5,6] to the end of the 5th traces marker.size -- leaving at most 10
# points per marker.size attribute
extendtraces!(p, Dict("marker.size"=>Vector[[1, 3], [5, 5, 6]]), [3, 5], 10)
```
