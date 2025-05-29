数演算子。

```jldoctest
julia> f = FockState(2)
|2⟩

julia> num = NumberOp()
n

julia> qsimplify(num*f, rewriter=qsimplify_fock)
2|2⟩
```
