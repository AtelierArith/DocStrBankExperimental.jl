```
MultiUniformRBFE(v::AbstractVector, Nv::Vector{Int}; normalize=false, coulomb=false)
```

Supply scheduling signal and number of basis functions For automatic selection of centers and widths

The keyword `normalize` determines whether or not basis function activations are normalized to sum to one for each datapoint, normalized networks tend to extrapolate better ["The normalized radial basis function neural network" DOI: 10.1109/ICSMC.1998.728118](http://ieeexplore.ieee.org/document/728118/)
