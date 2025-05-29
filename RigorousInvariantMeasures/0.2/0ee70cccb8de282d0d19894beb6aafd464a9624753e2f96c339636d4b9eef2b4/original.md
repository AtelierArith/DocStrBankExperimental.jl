```
mod1_dynamic(f::Function, ε = 0.0; full_branch = false)
```

Utility constructor for dynamics Mod 1 on the torus [0,1]. We assume that f is monotonic and differentiable, for now (this is not restrictive, for our purposes)

# Example

```jldoctest
julia> using RigorousInvariantMeasures;

julia> D0 = mod1_dynamic(x->2*x+0.5*x*(1-x), full_branch = true)
Piecewise-defined dynamic with 2 branches
```
