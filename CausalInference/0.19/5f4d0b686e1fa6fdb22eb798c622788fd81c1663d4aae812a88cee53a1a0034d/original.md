```
kl_entropy(data::Array{Float64, 2}; k=5)
```

Compute the nearest-neighbor estimate of the differential entropy of data.

data is a 2d array, with every column representing one data point.  For further information, see

"A class of Rényi information estimators for multidimensional densities" Nikolai Leonenko, Luc Pronzato, and Vippal Savani The Annals of Statistics, 2008 https://projecteuclid.org/euclid.aos/1223908088

keyword arguments: k=5: number of nearest neighbors
