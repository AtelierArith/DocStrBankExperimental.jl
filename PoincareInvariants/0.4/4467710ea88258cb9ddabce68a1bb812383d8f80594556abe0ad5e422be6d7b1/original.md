```
compute!(pinv::AbstractPoincareInvariant, points::AbstractVector{<:AbstractVector},
    times::Union{AbstractVector{<:Real}, Real}=NaN, p=nothing)
```

computes a Poincaré invariant, using the setup object `pinv`, at each time for a set of trajectories given by `points`.

`points` represents an AbstractVector of trajectories. Each element of `points` is a trajectory, which is itself an `AbstractVector` of some kind of iterable or vector. `times` is either a constant, like `NaN`, or a vector of the times at which the trajectories have been evaluated, i.e. the i-th phase space position in each trajectory was evaluated at time `times[i]`. `p` is an arbitrary optional parameter which is passed to the differential form, like the the time.
