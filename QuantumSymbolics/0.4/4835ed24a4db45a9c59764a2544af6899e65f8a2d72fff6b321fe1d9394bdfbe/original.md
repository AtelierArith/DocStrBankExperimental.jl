```
qsimplify(s; rewriter=nothing)
```

Manually simplify a symbolic expression of quantum objects. 

If the keyword `rewriter` is not specified, then `qsimplify` will apply every defined rule to the expression.  For performance or single-purpose motivations, the user has the option to define a specific rewriter for `qsimplify` to apply to the expression. The defined rewriters for simplification are the following objects:     - `qsimplify_pauli`     - `qsimplify_commutator`     - `qsimplify_anticommutator`     - `qsimplify_fock`

```jldoctest
julia> qsimplify(σʸ*commutator(σˣ*σᶻ, σᶻ))
(0 - 2im)Z

julia> qsimplify(anticommutator(σˣ, σˣ), rewriter=qsimplify_anticommutator)
2𝕀
```
