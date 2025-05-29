```
beta_bins(n::Int=10)
```

A Simple function that produces a vector of bins boundaries, useful for histograms. It adds bins on the left and right tails for extreme values (0 and 1), convenient for data suited for [`OrderedBeta`](@ref) models. 

```jldoctest
julia> beta_bins(3)
6-element Vector{Float64}:
 -0.3333333333333333
  2.220446049250313e-16
  0.3333333333333335
  0.6666666666666667
  1.0
  1.3333333333333333

julia> beta_bins([0, 0.5, 0.2, 0.6, 0.8, 1, 0.5, 0.4])
6-element Vector{Float64}:
 -0.3333333333333333
  2.220446049250313e-16
  0.3333333333333335
  0.6666666666666667
  1.0
  1.3333333333333333
```
