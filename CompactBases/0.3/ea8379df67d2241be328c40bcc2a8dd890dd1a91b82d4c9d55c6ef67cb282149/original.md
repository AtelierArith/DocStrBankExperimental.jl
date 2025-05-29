```
ExpKnotSet(k, a, b, N[, ml=k, mr=k, base=10, include0=true])
```

Construct an order-`k` knot spanning from `base^a` to `base^b` in `N` intervals, optionally including 0 as the left endpoint.

# Examples

```jldoctest
julia> ExpKnotSet(2, -4, 2, 7)
10-element ExpKnotSet{2,2,2,Float64,StepRangeLen{Float64,Base.TwicePrecision{Float64},Base.TwicePrecision{Float64}},Array{Float64,1}}:
   0.0
   0.0
   0.0001
   0.001
   0.01
   0.1
   1.0
  10.0
 100.0
 100.0
```
