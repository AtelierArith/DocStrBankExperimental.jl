```
LinearKnotSet(k, a, b, N[, ml=k, mr=k])
```

Construct an order-`k` linear knot set spanning from `a` to `b`, with `N` intervals.

# Examples

```jldoctest
julia> LinearKnotSet(2, 0, 1, 3)
6-element LinearKnotSet{2,2,2,Float64,StepRangeLen{Float64,Base.TwicePrecision{Float64},Base.TwicePrecision{Float64}}}:
 0.0
 0.0
 0.3333333333333333
 0.6666666666666666
 1.0
 1.0
```
