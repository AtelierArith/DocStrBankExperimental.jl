Abstract supertype of all state estimators.

---

```
(estim::StateEstimator)(d=[]) -> ŷ
```

Functor allowing callable `StateEstimator` object as an alias for [`evaloutput`](@ref).

# Examples

```jldoctest
julia> kf = KalmanFilter(setop!(LinModel(tf(3, [10, 1]), 2), yop=[20]), direct=false);

julia> ŷ = kf() 
1-element Vector{Float64}:
 20.0
```
