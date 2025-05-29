```
compute_nobs_matrix!(nobs_matrix::Vector{NobsMatrixElement}, observations::Vector{Observation{T}})
```

Initialize all the elements in `nobs_matrix` so that they are the matrices M_p in Eq. (10) of KurkiSuonio2009. The TOD is taken from the list of observations in the parameter `observations`.
