```julia
get_efms(N::Matrix{Float64}; tol) -> Any

```

Calculate elementary flux modes of a stoichiometric matrix. Input: `N`: the stoichiometric matrix of a network with only forward reactions. Output: matrix of the EFMs, each column is a different EFM, rows correspond to the reaction indices of the input `N`.
