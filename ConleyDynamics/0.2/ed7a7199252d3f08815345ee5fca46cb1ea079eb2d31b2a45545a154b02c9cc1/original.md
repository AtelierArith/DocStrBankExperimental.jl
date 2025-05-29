```
ConleyMorseCM{T}
```

Collect the connection matrix information in a struct.

The struct has the following fields:

  * `matrix::SparseMatrix{T}`: Connection matrix
  * `columns::Vector{Int}`: Corresponding columns in the boundary matrix
  * `poset::Vector{Int}`: Poset indices for the connection matrix columns
  * `labels::Vector{String}`: Labels for the connection matrix columns
  * `morse::Vector{Vector{String}}`: Vector of Morse sets in original complex
  * `conley::Vector{Vector{Int}}`: Vector of Conley indices for the Morse sets
  * `complex::LefschetzComplex`: The Conley complex as a Lefschetz complex
