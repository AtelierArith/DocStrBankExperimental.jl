```
kron_pow(x::Vector{<:AbstractVariable}, pow::Int)
```

高次の具体的なクロンカー冪を計算します: `x ⊗ x ⊗ ... ⊗ x`、`pow` 回、象徴的な単項式のベクトルに対して。

### 入力

  * `x`   – 多項式変数
  * `pow` – 整数

### 出力

`x^{⊗ pow}` に対応する多変数単項式のベクトル。

### 例

```jldoctest
julia> using DynamicPolynomials

julia> @polyvar x[1:2]
(PolyVar{true}[x₁, x₂],)

julia> x
2-element Vector{PolyVar{true}}:
 x₁
 x₂

julia> kron_pow(x, 2)
4-element Vector{Monomial{true}}:
 x₁²
 x₁x₂
 x₁x₂
 x₂²
```
