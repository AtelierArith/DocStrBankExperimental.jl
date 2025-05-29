```
randprobvec([rng, T=Float64], d)
```

Generates points of type `T`, uniformly at random on the standard `d-1` dimensional simplex using an algorithm by [Smith and Tromble](http://www.cs.cmu.edu/~nasmith/papers/smith+tromble.tr04.pdf).

## Example

```julia
julia> randprobvec(3)
3-element Array{Float64,1}:
 0.24815974900033688
 0.17199716455672287
 0.5798430864429402 

```
