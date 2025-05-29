Annihilation (lowering or destroy) operator in defined Fock basis.

```jldoctest
julia> f = FockState(2)
|2⟩

julia> destroy = DestroyOp()
a

julia> qsimplify(destroy*f, rewriter=qsimplify_fock)
(sqrt(2))|1⟩
```
