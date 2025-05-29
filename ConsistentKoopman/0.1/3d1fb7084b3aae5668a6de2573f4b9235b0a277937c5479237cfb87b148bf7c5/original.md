```
tune_bandwidth(D::Matrix{Float64},
 DN::Matrix{Integer}, NN::Integer,
 nT::Integer, epsls::Vector{Float64})

tune bandwidth function -> should make sure this works, the behavior is a lil funky
    fixed, is a small typo in the pseudo code I think (is missing a square?)

from 10.1016/j.acha.2017.09.001
probably cheating a bit by only taking the sum of the NN nearest neighbors
hoping it doesn't matter too much 

Arguments
=================
- D: precomputed distances for nearest neighbors NN (from distNN)
- DN: distance indexing information (also from distNN)
- NN: number of nearest neighbors
- nT: total time of processed data
- epsls: vector of test epsilons (strictly positive only)
```
