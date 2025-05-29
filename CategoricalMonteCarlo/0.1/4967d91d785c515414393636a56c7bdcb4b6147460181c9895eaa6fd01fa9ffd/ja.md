```
algorithm3_ratio(w::Vector{<:Real}, r::Real)
```

`w`を確率に正規化して作成された確率のベクトルを返し、次に、0の要素の合計と非ゼロ要素の合計の比が`r`に等しくなるように、確率質量`u = r / (1 + r)`を`w`の0またはそれ以上の要素に広げます。もし`w`のすべての値がゼロであり、`r ≠ 0`の場合、均一な確率質量のベクトルが返されます。

数学的には、次のように与えられます：

𝐰 ∈ ℝᴺ, 0 ≤ wᵢ < ∞, r ∈ ℝ, 0 ≤ r ≤ Inf, J = {i : 𝐰ᵢ = 0}

```
pᵢ =
    ケース 1: J ≠ ∅ の場合
            (r / (1+r)) / |J|                     もし i ∈ J
            (1 / (1+r)) * 𝐰ᵢ / ∑ᵢ₌₁ᴺ 𝐰ᵢ           それ以外
    ケース 2: J = {1,…,N} の場合
            r / (r * N)                           𝐰 ≠ ̲0 の場合は 1/N に相当
```

参照： [`algorithm3_ratio!`](@ref), [`algorithm3`](@ref)

# 例

```jldoctest
julia> w = Rational{Int}[1, 0, 3, 0, 5]; r = 3;

julia> p = algorithm3_ratio(w, r)
5-element Vector{Rational{Int64}}:
 1//36
 3//8
 1//12
 3//8
 5//36

julia> r′ = sum(p[findall(iszero, w)]) / sum(p[findall(!iszero, w)]); (r′, r′ == r)
(3//1, true)

julia> algorithm3(w, r / (1 + r))              # 等価性に注意
5-element Vector{Rational{Int64}}:
 1//36
 3//8
 1//12
 3//8
 5//36

julia> algorithm3_ratio(w, Inf)                # r = Inf ⟹ u = 1
5-element Vector{Rational{Int64}}:
 0//1
 1//2
 0//1
 1//2
 0//1
```
