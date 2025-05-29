```
split_weight(trees::Vector{HybridNetwork}, n::Int64)
```

Split-weight embedding of phylogenetic trees in a `Vector{HybridNetwork}`. Note that all taxa will be replaced by numbers. Use the function [`num_to_name`](@ref) to  get a Dictionary containing the name of the taxon corresponding to the number.

# Arguments

  * `trees`: a Vector of HybridNetwork objects that contains trees
  * `n`: the number of taxa of the trees

# Output

A `Matrix{Float64}` shows the trees in bipartiton format

# Example

```jldoctest
julia> split_weight([readTopology("(4:4.249,(1:2.457,(2:2.064,3:2.064):0.393):1.793);"), readTopology("(4:4.308,(2:1.634,(1:1.588,3:1.588):0.046):2.674);")], 4)
2×7 Matrix{Float64}:
 2.457  2.064  2.064  6.042  0.0  0.0    0.393
 1.588  1.634  1.588  6.982  0.0  0.046  0.0
```
