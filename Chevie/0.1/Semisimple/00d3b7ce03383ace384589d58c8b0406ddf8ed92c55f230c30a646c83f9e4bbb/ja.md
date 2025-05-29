`fundamental_group(W)`

この関数は、コクセター群構造 `W` によって定義された代数群の基本群を返します。この群は、対応するアフィン・ワイル群の図式自己同型の群として返され、これは単純根の集合の置換の群として表され、各不可約成分の最も低い根によって強化されています。私たちが取る冗長群の（必ずしも半単純でない）基本群の定義は、(P∩ Y(𝐓))/Q であり、ここで P はコウェイト格子（根格子の Y(𝐓)⊗ ℚ における双対格子）であり、Q はコルート格子です。P/Q の要素と図式自己同型との間の全単射は、例えば [§3.B Bonnafé2005](biblio.htm#Bon05) の文脈で非可約群に関して説明されています。

```julia-repl
julia> W=coxgroup(:A,3) # 隣接群
A₃

julia> fundamental_group(W) # 12乗根が最も低いもの
Group((1,12,3,2))

julia> W=rootdatum(:sl,4) # 半単純単連結群
sl₄

julia> fundamental_group(W)
Group(Perm{Int16}[])
```
