```
octave(community_matrix::Community_Matrix, community_selected::String)
```

Compute the octave distribution of species in a selected community.

# Arguments

  * `community_matrix::Community_Matrix`: The input community matrix.
  * `community_selected::String`: The name of the community for which the octave distribution is to be computed.

# Returns

A tuple `(community_name, community_ranked)` where:

  * `community_name` is the name of the selected community.
  * `community_octave` is a DataFrame containing the species abundance and their corresponding octave class.

# Details

This function computes the octave distribution of species abundance within a selected community from the input community matrix.  The octave distribution categorizes species abundance into octave classes, with each class representing a doubling in abundance. 

See also [`octave_plot`](@ref),
