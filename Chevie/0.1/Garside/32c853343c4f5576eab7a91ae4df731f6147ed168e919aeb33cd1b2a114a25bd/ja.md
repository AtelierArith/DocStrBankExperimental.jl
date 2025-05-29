`Category(atomsfrom::Function,o;action::Function=^)`

は、初期オブジェクト `o` と、オブジェクト `o` から原子を "マップ" `m` として返す関数 `atomsfrom(o)` からカテゴリを構築します。ターゲットオブジェクトは `action(o,m)` です。

例として、`G₃₁` のブレイド群に関連するガーサイドカテゴリを構築します。これは、双対ブレイドモノイド `E₈` における `δ³⁰` の4乗根の中心化子として実現されます。つまり、2分割カテゴリにおける `δad¹⁵` の不変点です。

```julia-repl
julia> W=coxgroup(:E,8);M=DualBraidMonoid(W)
DualBraidMonoid(E₈,c=[1, 4, 6, 8, 3, 2, 5, 7])

julia> s4=left_divisors(M,M.δ,4); # 長さ4の単純元

julia> s=M(s4[findfirst(x->x*δad(M,x,8)==M.δ,s4)])#2分割カテゴリのオブジェクト
(1 8 17 35)

julia> "the right-lcms of the `δⁱ`-orbits on `leftdescents(b)`"
       function satoms(b,i)
         M=b.M
         ld=M.atoms[leftdescents(b)]
         di=Perm(ld,δad.(Ref(M),ld,i))
         if isnothing(di) error(b," is not δ^$i-stable") end
         map(o->M(rightlcm(M,ld[o]...)),orbits(di,eachindex(ld)))
       end
satoms

julia> Category(x->satoms(x,15),s;action=(o,m)->inv(m)*o*δad(m,8))
category with 88 objects and 660 generating maps
```
