```
algorithm3(w::Vector{<:Real}, u::Real)
```

`w`を確率に正規化し、`0 ≤ u ≤ 1`の確率質量を`w`の中でゼロに等しい0個以上の要素に広げることによって作成された確率のベクトルを返します。もし`w`のすべての値がゼロであり、`u ≠ 0`であれば、一様確率質量のベクトルが返されます。

数学的には、次のように与えられます：

𝐰 ∈ ℝᴺ, 0 ≤ wᵢ < ∞, u ∈ ℝ, 0 ≤ u ≤ 1, J = {i : 𝐰ᵢ = 0}

```
pᵢ =
    ケース 1: J ≠ ∅ の場合
            u / |J|                     もし i ∈ J
            (1 - u) * 𝐰ᵢ / ∑ᵢ₌₁ᴺ 𝐰ᵢ     それ以外の場合
    ケース 2: J = {1,…,N} の場合
            u / (u * N)                 𝐰 ≠ ̲0 の場合は 1/N に相当
```

参照: [`algorithm3!`](@ref), [`algorithm3_ratio`](@ref)

# 例

```jldoctest
julia> algorithm3([0, 10, 5, 0], 0.5)
4-element Vector{Float64}:
 0.25
 0.3333333333333333
 0.16666666666666666
 0.25

julia> algorithm3(Rational{Int}[0, 0, 0], 0.25)    # 𝐰 = ̲0
3-element Vector{Rational{Int64}}:
 1//3
 1//3
 1//3

julia> algorithm3([0, 0], 0.0)                     # 𝐰 = ̲0 かつ u = 0
2-element Vector{Float64}:
 NaN
 NaN

julia> algorithm3([1, 2, 3], 0.9)                  # ゼロがない場合は単に正規化
3-element Vector{Float64}:
 0.16666666666666666
 0.3333333333333333
 0.5
```
