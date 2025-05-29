```
algorithm2_2(Is::NTuple{M, Vector{Int}}, ws::NTuple{M, Vector{<:Real}}) where {M}

それぞれのインデックスセット `Is` によって選択された重みの積を計算し、結果の重みベクトルを確率に正規化します。

数学的には、次のように与えられます：

I₁ ∈ ℕᴺ , 𝐰₁ ∈ ℝᴰ¹,     0 ≤ 𝐰₁ᵢ < Inf, i ∈ I₁

I₂ ∈ ℕᴺ , 𝐰₂ ∈ ℝᴰ²,     0 ≤ 𝐰₂ᵢ < Inf, i ∈ I₂

⋮       , ⋮

Iₘ ∈ ℕᴺ , 𝐰ₘ ∈ ℝᴰᵐ,     0 ≤ 𝐰ₘᵢ < Inf, i ∈ Iₘ

iᵗʰ 項は次のように計算されます： pᵢ = ∏ₘ₌₁ᴹ 𝐰ₘ[Iₘ[i]] / ∑ⱼ₌₁ᴺ ∏ₘ₌₁ᴹ 𝐰ₘ[Iₘ[j]]

参照： [`algorithm2_2!`](@ref), [`algorithm2_1`](@ref)

# 例

```

jldoctest julia> Is = ([1,2,3], [4,5,6], [7,8,9]); ws = ([1.0, 2.0, 3.0], fill(0.5, 6), fill(0.1, 9));

julia> algorithm2_2(Is, ws) 3-element Vector{Float64}:  0.16666666666666666  0.3333333333333333  0.5

julia> w = ws[1][Is[1]] .* ws[2][Is[2]] .* ws[3][Is[3]]    # 正規化されていない 3-element Vector{Float64}:  0.05  0.1  0.15000000000000002

julia> w ./= sum(w)                                        # 正規化された 3-element Vector{Float64}:  0.16666666666666666  0.3333333333333333  0.5 ```
