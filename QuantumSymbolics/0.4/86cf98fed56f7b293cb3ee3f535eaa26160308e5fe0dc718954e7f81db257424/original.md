Creation (raising) operator.

```jldoctest
julia> f = FockState(2)
|2⟩

julia> create = CreateOp()
a†

julia> qsimplify(create*f, rewriter=qsimplify_fock)
(sqrt(3))|3⟩
```
