`structure_rational_points_connected_centre(W,q)`

`W` はコクセター群または有限再帰群 $𝐆 ^F$ を表すコクセター余剰である必要があり、`q` は同型写像 `F` に関連する素数の冪である必要があります。この関数は、有限アーベル群 $Z⁰𝐆 ^F$ のアーベル不変量を返します。ここで `Z⁰𝐆` は `𝐆` の連結中心です。

以下の例では、`𝐓(𝔽₃)` の構造を決定します。ここで `𝐓` は `SL`₄ のすべての最大トーリにわたります。

```julia-repl
julia> l=twistings(rootdatum(:sl,4),Int[])
5-element Vector{Spets{FiniteCoxeterSubGroup{Perm{Int16},Int64}}}:
 A₃₍₎=Φ₁³
 A₃₍₎=Φ₁²Φ₂
 A₃₍₎=Φ₁Φ₂²
 A₃₍₎=Φ₁Φ₃
 A₃₍₎=Φ₂Φ₄

julia> structure_rational_points_connected_centre.(l,3)
5-element Vector{Vector{Int64}}:
 [2, 2, 2]
 [2, 8]
 [4, 8]
 [26]
 [40]
```
