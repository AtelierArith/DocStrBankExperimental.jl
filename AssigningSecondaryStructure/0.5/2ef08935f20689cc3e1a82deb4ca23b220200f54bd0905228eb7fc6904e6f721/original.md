```
assign_secondary_structure(chain_backbone::Array{T,3}}) where T<:Real
assign_secondary_structure(chain_backbones::Vector{Array{T,3}}) where T<:Real
```

Given a vector of chain backbones, each represented as a 3-dimensional array of size 3x3xL, this function assigns the secondary structure to each residue.

Returns a vector of vectors of integers, each of which is the secondary structure assignment for the corresponding chain and their respective residues. The secondary structure  encoded as follows:

  * `1`: loop (neither helix nor strand)
  * `2`: helix; α, 3_10, or π
  * `3`: strand; part of a β-sheet
