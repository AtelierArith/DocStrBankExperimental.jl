`class_polynomials(h::HeckeElt)`

は、Iwahori-Hecke代数の要素 `h` または `h.H` によって与えられるコセットのクラス多項式を返します。これは、コクセター群またはコセット `H.W` の共役類における最小長さの代表の集合 `R` に対する `T` 基底に関してです。この最小長さの代表は `classreps(H.W)` によって与えられます。これらの多項式のベクトル `p` は、もし `X` が `T_w` 上の `H` の不可約キャラクターの値の行列であるならば（`w∈ R` の場合）、積 `X*p` が `h` 上の不可約キャラクターの値のリストであるという性質を持っています。

```julia-repl
julia> W=coxsym(4)
𝔖 ₄

julia> H=hecke(W,Pol(:q))
hecke(𝔖 ₄,q)

julia> h=Tbasis(H,longest(W))
T₁₂₁₃₂₁

julia> p=class_polynomials(h)
5-element Vector{Pol{Int64}}:
 0
 0
 q²
 q³-2q²+q
 q³-q²+q-1
```

クラス多項式は [Geck-Pfeiffer1993](biblio.htm#GP93) で導入されました。
