`algebraic_center(W)`

`W` は Weyl 群、または拡張 Weyl 群である必要があります。この関数は、`W` によって定義される代数群 `𝐆` の中心 `Z` の説明を、以下のフィールドを持つ名前付きタプルとして返します。

`Z0`: 中立成分 `Z⁰` を `𝐓` の部分トーラスとして表します。

`AZ`: セミシンプル要素の群として与えられる `A(Z):=Z/Z⁰` の `Z` における代表。

`ZD`: セミシンプル要素の群として与えられる `𝐆` の導出部分群の中心。

`descAZ`: `W` が拡張 Weyl 群でない場合、単連結被覆 `𝐆` の中心 `pi` の商として `A(Z)` を説明します（基本群の一形態）。商写像の核を生成する `pi` の生成子における単語として与えられる要素のリストを含みます。

```julia_repl
julia> G=rootdatum(:sl,4)
sl₄

julia> L=reflection_subgroup(G,[1,3])
A₃₍₁₃₎=A₁×A₁

julia> C=algebraic_center(L)
(Z0 = SubTorus(A₃₍₁₃₎=A₁×A₁Φ₁,[1 2 1]), AZ = Group(SemisimpleElement{Root1}[<1,1,-1>]), descAZ = [[1, 2]], ZD = Group(SemisimpleElement{Root1}[<-1,1,1>, <1,1,-1>]))

julia> G=coxgroup(:A,3)
A₃

julia> s=ss(G,[0,1//2,0])
SemisimpleElement{Root1}: <1,-1,1>

julia> C=centralizer(G,s)
A₃₍₁₃₎=(A₁A₁)Φ₂

julia> algebraic_center(C)
(Z0 = SubTorus(A₃₍₁₃₎=A₁×A₁Φ₁,Matrix{Int64}(undef, 0, 3)), AZ = Group(SemisimpleElement{Root1}[<1,-1,1>]))
```
