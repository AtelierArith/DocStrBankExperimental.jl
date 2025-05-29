`word(W::CoxeterGroup,w)`

は、コクセター群 `W` の標準生成子における要素 `w` の縮約語を返します（対応する生成子のインデックスのベクトルとして表現されます）。

```julia-repl
julia> W=coxgroup(:A,3)
A₃

julia> w=perm"(1,11)(3,10)(4,9)(5,7)(6,12)"
(1,11)(3,10)(4,9)(5,7)(6,12)

julia> w in W
true

julia> word(W,w)
5-element Vector{Int64}:
 1
 2
 3
 2
 1
```

`word` の結果は、`w` のための辞書順で最小の縮約語です（`gens(W)` によって与えられるコクセター生成子の順序に基づいています）。
