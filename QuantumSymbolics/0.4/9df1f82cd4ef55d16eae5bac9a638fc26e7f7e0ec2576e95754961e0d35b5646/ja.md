定義されたフォック基底における消滅（低下または破壊）演算子。

```jldoctest
julia> f = FockState(2)
|2⟩

julia> destroy = DestroyOp()
a

julia> qsimplify(destroy*f, rewriter=qsimplify_fock)
(sqrt(2))|1⟩
```
