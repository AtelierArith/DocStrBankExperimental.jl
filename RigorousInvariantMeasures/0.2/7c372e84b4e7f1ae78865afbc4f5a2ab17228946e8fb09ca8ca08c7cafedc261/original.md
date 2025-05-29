```
max_distortion(D::PwMap; tol=1e-3)
```

Compute a rigorous bound for the distortion of a PwMap

# Example

```jldoctest
julia> using RigorousInvariantMeasures;

julia> D0 = mod1_dynamic(x->2*x+0.5*x*(1-x), full_branch = true)
Piecewise-defined dynamic with 2 branches

julia> max_distortion(D0)
[0.444268, 0.444445]
```
