Displacement operator in defined Fock basis.

```jldoctest
julia> f = FockState(0)
|0⟩

julia> displace = DisplaceOp(im)
D(im)

julia> qsimplify(displace*f, rewriter=qsimplify_fock)
|im⟩
```
