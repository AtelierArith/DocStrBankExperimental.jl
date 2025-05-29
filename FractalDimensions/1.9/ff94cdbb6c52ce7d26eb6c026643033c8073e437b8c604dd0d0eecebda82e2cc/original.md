```
molteno_boxing(X::AbstractStateSpaceSet; k0::Int = 10) → (probs, εs)
```

Distribute `X` into boxes whose size is halved in each step, according to the algorithm by [Molteno1993](@cite). Division stops if the average number of points per filled box falls below the threshold `k0`.

Return `probs`, a vector of [`Probabilities`](@ref) of finding points in boxes for different box sizes, and the corresponding box sizes `εs`. These outputs are used in [`molteno_dim`](@ref).

## Description

Project the `data` onto the whole interval of numbers that is covered by `UInt64`. The projected data is distributed into boxes whose size decreases by factor 2 in each step. For each box that contains more than one point `2^D` new boxes are created where `D` is the dimension of the data.

The process of dividing the data into new boxes stops when the number of points over the number of filled boxes falls below `k0`. The box sizes `εs` are calculated and returned together with the `probs`.

This algorithm is faster than the traditional approach of using `ValueHistogram(ε::Real)`, but it is only suited for low dimensional data since it divides each box into `2^D` new boxes if `D` is the dimension. For large `D` this leads to low numbers of box divisions before the threshold is passed and the divison stops. This results to a low number of data points to fit the dimension to and thereby a poor estimate.
