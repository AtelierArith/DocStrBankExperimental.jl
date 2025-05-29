Abstract supertype of all predictive controllers.

---

```
(mpc::PredictiveController)(ry, d=[]; kwargs...) -> u
```

Functor allowing callable `PredictiveController` object as an alias for [`moveinput!`](@ref).

# Examples

```jldoctest
julia> mpc = LinMPC(LinModel(tf(5, [2, 1]), 3), Nwt=[0], Hp=1000, Hc=1, direct=false);

julia> u = mpc([5]); round.(u, digits=3)
1-element Vector{Float64}:
 1.0
```
