```julia
RandomStreamDataset(T, d, n, f)
RandomStreamDataset(T, d, n, f, rng)

```

A dataset generated randomly and on the fly, but with a fixed seed so that it can be iterated over multiple times. It is possible to iterate over a RandomStreamDataset using a `BatchIterator` from BatchIterators package. Parameter `f` should be a function which for parameters (i::Int, rng::MersenneTwister) returns a `d`×`i` matrix of elements of type `T`. The random number generator should be used sequentially, so that f(2,rng) should be the same as concatening the results of two calls to f(1,rng). 
