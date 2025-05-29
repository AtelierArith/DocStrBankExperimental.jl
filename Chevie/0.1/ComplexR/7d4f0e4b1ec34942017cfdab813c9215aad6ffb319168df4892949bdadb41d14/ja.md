`Reflection` は、反射群における反射を表す `struct` です。

```julia-repl
julia> W=crg(8);

julia> r=reflections(W)[7] # (r.W,r.rootno,r.eigen) を表示
Reflection(G₈,1,-1)

julia> r.rootno # r は最初の根に対する反射
1

julia> r.eigen # 非自明な固有値、Root1 として
Root1: -1

julia> r.W # r が反射である群
G₈

julia> r==Reflection(W,1,-1) # .rootno と .eigen で r を指定
true

julia> Reflection(W,1) # .rootno で指定すると特別な反射が得られる
Reflection(G₈,1,ζ₄)

julia> root(r)
2-element Vector{Cyc{Rational{Int64}}}:
  0
 ζ₄

julia> coroot(r)
2-element Vector{Cyc{Int64}}:
    0
 -2ζ₄

julia> Matrix(r)
2×2 Matrix{Cyc{Rational{Int64}}}:
 1   0
 0  -1

julia> hyperplane(r) # 固定された超平面、行空間として
1×2 Matrix{Cyc{Rational{Int64}}}:
 1  0

julia> hyperplane(r)*Matrix(r)==hyperplane(r)
true

julia> isdistinguished(r) # r は特別ではない
false

julia> exponent(r) # 特別な反射の何乗であるか
2

julia> Perm(r)
(1,8)(2,9)(3,16)(4,15)(5,17)(6,18)(7,19)(10,22)(11,21)(12,23)

julia> hyperplane_orbit(r) # r は最初の超平面軌道にある
1

julia> position_class(r) # W における r の共役類のインデックス
15

julia> simple_rep(r) # 共役反射を持つ最小の根インデックス
1

julia> word(r) # r のための r.W の生成子における単語
2-element Vector{Int64}:
 1
 1
```
