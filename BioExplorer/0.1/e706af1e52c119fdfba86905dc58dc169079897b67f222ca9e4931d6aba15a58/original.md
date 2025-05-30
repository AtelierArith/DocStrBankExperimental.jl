```
mat_com_convert(community_matrix::Community_Matrix)
```

Convert a community matrix with abundance data to a community matrix with incidence data.

# Arguments

  * `community_matrix::Community_Matrix`: The input community matrix with abundance data.

# Returns

  * The corresponding community matrix with incidence data.

# Details

The function converts a community matrix with abundance data to a community matrix with incidence data by replacing abundance values greater than 0 with 1 (indicating presence) and leaving abundance values of 0 unchanged (indicating absence).  The resulting matrix has the same structure as the input matrix but with incidence data.
