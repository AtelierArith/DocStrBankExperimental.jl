Squeezing operator in defined Fock basis.

```jldoctest
julia> S = SqueezeOp(pi)
S(π)

julia> qsimplify(S*vac, rewriter=qsimplify_fock)
|0,π⟩
```
