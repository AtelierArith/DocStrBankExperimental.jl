フォック基底で定義された変位演算子。

```jldoctest
julia> f = FockState(0)
|0⟩

julia> displace = DisplaceOp(im)
D(im)

julia> qsimplify(displace*f, rewriter=qsimplify_fock)
|im⟩
```
