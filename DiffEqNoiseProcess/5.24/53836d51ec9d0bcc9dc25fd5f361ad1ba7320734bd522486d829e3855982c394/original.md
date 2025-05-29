```julia
BoxWedgeTail{T, N, Tt, TA, T2, T3, ZType, F, F2, inplace, RNGType, tolType, spacingType,
    jpdfType, boxType, wedgeType, tailType, distBWTType, distΠType} <:
AbstractNoiseProcess{T, N, Vector{T2}, inplace}
```

The method for random generation of stochastic area integrals due to Gaines and Lyons. The method is based on Marsaglia's "rectangle-wedge-tail" approach for two dimensions.

3 different groupings for the boxes are implemented.

  * box_grouping = :Columns (full, i.e., as large as possible, columns on a square spanned by dr and da)
  * box_grouping = :none (no grouping)
  * box_grouping = :MinEntropy (default, grouping that achieves a smaller entropy than the column wise grouping and thus allows for slightly faster sampling – but has a slightly larger number of groups)

The sampling is based on the Distributions.jl package, i.e., to sample from one of the many distributions, a uni-/bi-variate distribution from Distributions.jl is constructed, and then rand(..) is used.

## Constructor

```julia
BoxWedgeTail{iip}(t0, W0, Z0, dist, bridge;
    rtol = 1e-8, nr = 4, na = 4, nz = 10,
    box_grouping = :MinEntropy,
    sqeezing = true,
    save_everystep = true,
    rng = Xorshifts.Xoroshiro128Plus(rand(UInt64)),
    reset = true, reseed = true) where {iip}
```
