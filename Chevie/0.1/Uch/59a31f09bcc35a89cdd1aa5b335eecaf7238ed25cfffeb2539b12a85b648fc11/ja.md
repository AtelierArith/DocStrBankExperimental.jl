`cuspidal_data(W[,d[,ad]];proper=false,all=false)`

は、名前付きタプル `(levi=LF,cuspidal=λ,d=d)` を返します。ここで `LF` は `d`-分割レヴィであり（`ad` が与えられた場合、次元 `ad` の `d`-中心を持ちます）、`λ` は `LF` の `d`-カスピダル文字です。`d=1` の場合、通常のカスピダル文字が返されます。文字 `λ` は、非可換文字のリストにおけるそのインデックスとして与えられます。`d` が整数として与えられた場合、それは `E(d)` を表す `Root1` として返されます。

キーワード `proper=true` が与えられた場合、`LF!=W`（または同等に `ad>0`）であるデータのみが返されます。

`d` が省略された場合、`W` の要素の固有値のすべての `d` 順序のデータが返されます。さらにキーワード引数 `all=true` が与えられた場合、`W` の要素のすべての固有値のデータが返されます。

```julia-repl
julia> cuspidal_data(coxgroup(:F,4),1)
9-element Vector{@NamedTuple{levi::Spets{FiniteCoxeterSubGroup{Perm{Int16},Int64}}, cuspidal::Int64, d::Root1}}:
 (levi = F₄, cuspidal = 31, d = 1)
 (levi = F₄, cuspidal = 32, d = 1)
 (levi = F₄, cuspidal = 33, d = 1)
 (levi = F₄, cuspidal = 34, d = 1)
 (levi = F₄, cuspidal = 35, d = 1)
 (levi = F₄, cuspidal = 36, d = 1)
 (levi = F₄, cuspidal = 37, d = 1)
 (levi = F₄₍₂₃₎=B₂₍₂₁₎Φ₁², cuspidal = 6, d = 1)
 (levi = F₄₍₎=Φ₁⁴, cuspidal = 1, d = 1)

julia> cuspidal_data(complex_reflection_group(4),3)
5-element Vector{@NamedTuple{levi::Spets{PRSG{Cyc{Rational{Int64}}, Int16}}, cuspidal::Int64, d::Root1}}:
 (levi = G₄, cuspidal = 3, d = ζ₃)
 (levi = G₄, cuspidal = 6, d = ζ₃)
 (levi = G₄, cuspidal = 7, d = ζ₃)
 (levi = G₄, cuspidal = 10, d = ζ₃)
 (levi = G₄₍₎=Φ₁Φ′₃, cuspidal = 1, d = ζ₃)
```
