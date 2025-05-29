```
residues(pq::AbstractRationalFunction; method=:numerical,  kwargs...)
```

`p/q =d + r/q` の場合、`d` と有理数の残差 `r/q` を返します。

まず `divrem` を通じて `p/q =d + r/q` を `q` よりも次数の低い `r` で表現します。次に `r/q` の極を見つけます。重複度 `k` の極 `λj` に対して、`k` 個の残差 `rⱼ[k]/(z-λⱼ)^k`、`rⱼ[k-1]/(z-λⱼ)^(k-1)`、`rⱼ[k-2]/(z-λⱼ)^(k-2)`、…、`rⱼ[1]/(z-λⱼ)` があります。残差は次の式を使って求められます：`1/j! * dʲ/dsʲ (F(s)(s - λⱼ)^k` を `λⱼ` で評価したものです ([5-28](https://stanford.edu/~boyd/ee102/rational.pdf))。

## 例

(上記のPDFのページ5-33から)

```jldoctest rational_functions
julia> using Polynomials


julia> s = variable(Polynomial, :s)
Polynomial(1.0*s)

julia> pq = (-s^2 + s + 1) // ((s-1) * (s+1)^2)
(1.0 + 1.0*s - 1.0*s^2) // (-1.0 - 1.0*s + 1.0*s^2 + 1.0*s^3)

julia> d,r = residues(pq);


julia> d
Polynomial(0.0)

julia> r
Dict{Float64, Vector{Float64}} with 2 entries:
  -1.0 => [-1.25, 0.5]
  1.0  => [0.25]

julia> iszero(d)
true

julia> z = variable(pq)
(1.0*s) // (1.0)

julia> for (λ, rs) ∈ r # `residues` の出力から p/q を再構築
           for (i,rᵢ) ∈ enumerate(rs)
               d += rᵢ/(z-λ)^i
           end
       end


julia> p′, q′ = lowest_terms(d);


julia> q′ ≈ (s-1) * (s+1)^2 # 動作します、q は単項式です
true

julia> p′ ≈ (-s^2 + s + 1)
true
```

!!! 注     数値的な問題が発生する可能性のあるいくつかの領域があります。`divrem`、重複根の特定（`multroot`）、導関数の評価などです。
