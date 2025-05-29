```
    solveQP(Q::QP{T}; settings, settingsLP) where T
    solveQP(V::Matrix{T}, q::Vector{T}, A, b, G, g, d, u; settings, settingsLP) where T
    solveQP(Q::QP{T}, S::Vector{Status}, x0; settings) where T
```

for quadratic programming problems: the initial feasible point (S, x0) if given,  can be obtained from SimplexLP

$$
    min   (1/2)z′Vz+q′z
    s.t.   Az=b ∈ R^{M}
           Gz≤g ∈ R^{J}
           d≤z≤u ∈ R^{N}
$$

Outputs

```
z               : solution,  N x 1 vector
S               : Vector{Status}, (N+J)x1
status          : > 0 if successful (=iter_count); = 0 if infeasibility detected; < 0 fail (=-1 if numerical error, =-maxIter if not converged)
```

See also [`QP`](@ref), [`SimplexLP`](@ref), [`Settings`](@ref), [`initQP`](@ref), [`initSSQP`](@ref)
