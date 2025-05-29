```markdown
shrink(l::Vector{<:GarsideElt})

リスト `l` は、同じガーサイド群 `G` の要素のリストです。この関数は、要素 `l` によって生成される `G` の部分群の別の生成系を、合計の長さが小さいものを見つけようとします（長さは関数 `word` によって返されるものとしてカウントされます）。これは、`centralizer_gens` の結果を簡素化したり、他のブレイド部分群に使用することができます。

```

julia-repl julia> B=BraidMonoid(coxsym(3)) BraidMonoid(𝔖 ₃)

julia> b=[B(1)^3,B(2)^3,B(-2,-1,-1,2,2,2,2,1,1,2),B(1,1,1,2)] 4-element Vector{GarsideElt{Perm{Int16}, BraidMonoid{Perm{Int16}, CoxSym{Int16}}}}:  1.1.1  2.2.2  (1.12)⁻¹2.2.2.21.12  1.1.12

julia> shrink(b) 2-element Vector{GarsideElt{Perm{Int16}, BraidMonoid{Perm{Int16}, CoxSym{Int16}}}}:  2  1

```

```
