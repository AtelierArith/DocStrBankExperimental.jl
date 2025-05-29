フォック基底で定義された圧縮演算子。

```jldoctest
julia> S = SqueezeOp(pi)
S(π)

julia> qsimplify(S*vac, rewriter=qsimplify_fock)
|0,π⟩
```
