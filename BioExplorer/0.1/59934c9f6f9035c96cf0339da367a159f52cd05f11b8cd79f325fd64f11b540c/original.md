```
SAC(community_matrix::Community_Matrix, npermut::Int64 = 0)
```

Compute the species accumulation curve for a community matrix.

# Arguments

  * `community_matrix::Community_Matrix`: The input community matrix.
  * `npermut::Int64`: The number of permutations for computing confidence intervals around the mean accumulation curve. Defaults to 0, indicating no permutation.

# Returns

  * If `npermut` is 0, returns a vector representing the species accumulation curve.
  * If `npermut` is greater than 0, returns a DataFrame containing the mean accumulation curve and confidence intervals.
  * Makie Figure representing the species accumulation curve.

# Details

The function computes the species accumulation curve for the input community matrix.  If `npermut` is greater than 0, it performs permutations of the community matrix and computes multiple accumulation curves to estimate confidence intervals around the mean accumulation curve.  The function generates a plot of the accumulation curve and displays it.
