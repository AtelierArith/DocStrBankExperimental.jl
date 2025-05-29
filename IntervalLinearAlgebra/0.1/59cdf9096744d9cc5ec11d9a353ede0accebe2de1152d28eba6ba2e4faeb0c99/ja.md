```
epsilon_inflation(A::AbstractMatrix{T}, b::AbstractArray{S, N};
                  r=0.1, ϵ=1e-20, iter_max=20) where {T<:Real, S<:Real, N}

epsilon_inflation(A::AbstractMatrix{T}, b::AbstractArray{S, N};
                  r=0.1, ϵ=1e-20, iter_max=20) where {T<:Interval, S<:Interval, N}
```

$$
Ax=b
$$

の平方線形システムの解の包絡を ϵ-インフレーションアルゴリズムを使用して提供します。詳細は [[RUM10]](@ref) のアルゴリズム 10.7 を参照してください。

### 入力

  * `A`        – サイズ n × n の正方行列
  * `b`        – 長さ n のベクトルまたはサイズ n × m の行列
  * `r`        – 相対インフレーション、デフォルトは 10%
  * `ϵ`        – 絶対インフレーション、デフォルトは 1e-20
  * `iter_max` – 最大反復回数

### 出力

  * `x`    – 線形システムの解の包絡
  * `cert` – ブールフラグ。`cert==true` の場合、`x` は線形システムの真の解を含むことが*証明された*ことを示します。`cert==false` の場合、アルゴリズムは $x$ が実際に真の解を含むことを証明できませんでした。

### アルゴリズム

実数システム $Ax=b$ と近似解 $̃x$ が与えられたとき、$x₀ = [̃x, ̃x]$ で初期化します。各反復でアルゴリズムはインフレーションを計算します。

$$
y = xₖ * [1 - r, 1 + r] .+ [-ϵ, ϵ]
$$

および更新を行います。

$$
xₖ₊₁ = Z + (I - CA)y
$$

、

ここで $Z = C(b - Ax₀)$ であり、$C$ は $A$ の近似逆行列です。条件 $xₖ₊₁ ⊂ y$ が満たされると、$xₖ₊₁$ は $A⁻¹b$ の証明された包絡となり、`cert` は true に設定されます。条件が最大反復回数まで満たされない場合、最新の計算された包絡が返されますが、$cert$ は false に設定され、アルゴリズムは包絡が真の解を含むことを証明できなかったことを意味します。区間システムの場合、$̃x$ は $A$ と $b$ の中点を考慮して得られます。

### 注意事項

  * このアルゴリズムは *実数* 線形システム、または非常に小さな区間を持つ区間システムを対象としています。より広い区間を持つ区間線形システムについては、[`solve`](@ref) 関数を参照してください。

### 例

```jldoctest
julia> A = [1 2;3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> b = A * ones(2)
2-element Vector{Float64}:
 3.0
 7.0

julia> x, cert = epsilon_inflation(A, b)
(Interval{Float64}[[0.999999, 1.00001], [0.999999, 1.00001]], true)

julia> ones(2) .∈ x
2-element BitVector:
 1
 1

julia> cert
true
```
