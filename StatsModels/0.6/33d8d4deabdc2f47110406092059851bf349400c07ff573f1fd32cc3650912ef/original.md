```
HypothesisCoding(hypotheses::Vector{Pair}; levels=nothing)
```

Specify hypotheses as a vector of `label=>hypothesis_vector` pairs.  Labels are generated from the keys of the pairs.  The `levels` argument provides the names of the levels for each entry in the hypothesis vectors.  If omitted, the `levels` function will be called on the data when constructing a `ContrastsMatrix`

# Example

```jldoctest
julia> hc = HypothesisCoding(["a_and_b" => [1, 1, 0], "b_and_c" => [0, 1, 1]]);

julia> hc.hypotheses
2×3 Array{Int64,2}:
 1  1  0
 0  1  1

julia> hc.labels
2-element Array{String,1}:
 "a_and_b"
 "b_and_c"
```
