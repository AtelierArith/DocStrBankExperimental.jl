```
num_to_name(tree::HybridNetwork)
```

Obtain a table that contains taxon numbers and their names for a given tree.

# Arguments

  * `tree`: a HybridNetwork objects that contains trees

# Output

A `Dict{Int64, Any}` shows taxon numbers and their names

# Example

```jldoctest
julia> num_to_name(readTopology("(O:3.866,(HYB:1.593,(P1:1.208,P2:1.208):0.386):2.273);"))
Dict{Int64, Any} with 4 entries:
  4 => "P2"
  2 => "O"
  3 => "P1"
  1 => "HYB"
```
