`conjugating_elt(b,b₁[,F];ss=Val(:sc))`

`b` と `b₁` は同じガーサイド群の要素である必要があります。この関数は、`b^a=b₁` となる `a` を返します。もしそのようなものが存在しない場合は `nothing` を返します。引数 `ss` が与えられた場合、計算は対応するカテゴリで行われます –- [`conjcat`](@ref) を参照してください。引数 `F` が与えられた場合、それは `b.M.W` に付随する反射コセットのフロベニウスのようなブレイドモノイドの自己同型である必要があります。その場合、計算は対応する `F`-共役カテゴリで行われます。

```julia-repl
julia> W=coxgroup(:D,4)
D₄

julia> B=BraidMonoid(W)
BraidMonoid(D₄)

julia> b=B(2,3,1,2,4,3)
231243

julia> b1=B(1,4,3,2,2,2)
1432.2.2

julia> conjugating_elt(b,b1)
(134312.23)⁻¹

julia> c=conjugating_elt(b,b1;ss=Val(:cyc))
232.2

julia> b^c
1432.2.2

julia> WF=spets(W,Perm(1,2,4))
³D₄

julia> F=Frobenius(WF);

julia> c=B(3,4,3,1,2,3)
343123

julia> conjugating_elt(b,c,F)
124312

julia> ^(b,B(1,2,4,3,1,2),F)
343123
```
