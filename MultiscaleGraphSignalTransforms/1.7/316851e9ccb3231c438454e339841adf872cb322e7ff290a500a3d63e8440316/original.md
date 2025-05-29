```
sort_wavelets(A; onlyByLoc = false)
```

sort A's column wavelet vectors based on their focused nodes' indices. flip signs via the cross correlation.

# Input Arguments

  * `A::Matrix{Float64}`: whose column vectors are wavelets.

# Output Argument

  * `A::Matrix{Float64}`: a matrix with sorted and sign flipped column.
