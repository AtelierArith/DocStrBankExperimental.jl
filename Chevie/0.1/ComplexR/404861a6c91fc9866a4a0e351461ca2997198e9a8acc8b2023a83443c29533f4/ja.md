`complex_reflection_group(STnumber)` または `crg(STnumber)`

`complex_reflection_group(p,q,r)` または `crg(p,q,r)`

最初の形式の `complex_reflection_group` は、Shephard-Todd番号 `STnumber` を持つ複素反射群を返します。詳細は [Shephard-Todd1954](biblio.htm#ST54) を参照してください。2番目の形式は、非原始的複素反射群 `G(p,q,r)` を返します。

```julia-repl
julia> G=complex_reflection_group(4)
G₄

julia> degrees(G)
2-element Vector{Int64}:
 4
 6

julia> length(G)
24

julia> W*coxgroup(:A,2) # 非可約群を作成する方法
G₄×A₂

julia> complex_reflection_group(1,1,3) # A₂を入力する別の方法
gl₃

julia> crg(4) # 短いエイリアスもあります
G₄
```
