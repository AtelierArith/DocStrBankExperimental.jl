```
optimaltransportation(M::AbstractArray;
        [a, b, λ=1, ϵ=1e-10, maxiter=100])
```

Performs optimal transportation on an ecological network. Here, `M` is treated as an utility matrix, quantifying the preference the species of the two throphic levels have for interacting with another. One can fix both, one or none of the species abundances by given `a` (row sums, corresponding to top species) and/or `b` (column sums, corresponding to bottom species). The strengh of entropic  regularisation is set by `λ`, where higher values indicate more utitlity and lower values more entropy. 

ϵ and `maxiter` control the number of Sinkhorn iterations. You likely won't need to change these.

This version works on arrays.

Stock, M., Poisot, T., & De Baets, B. (2021). « Optimal transportation theory for species interaction networks. » Ecology and Evolution, 00(1), ece3.7254. https://doi.org/10.1002/ece3.7254
