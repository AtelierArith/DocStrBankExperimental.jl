```julia
struct BisectorDefuzzifier <: FuzzyLogic.AbstractDefuzzifier
```

Bisector defuzzifier. Given the aggregated output function $f$ and the output variable domain $[a, b]$ the defuzzified output is the value $t ∈ [a, b]$ that divides the area under $f$ into two equal parts. That is

$$
∫_a^tf(x)\textrm{d}x = ∫_t^af(x)\textrm{d}x.
$$

### Parameters

  * `N::Int64`: number of subintervals for integration, default 100.

## Algorithm

The domain is partitioned into N equal subintervals. For each subinterval endpoint, the left and right area are approximated using the trapezoidal rule. The end point leading to the best approximation is the final result.
