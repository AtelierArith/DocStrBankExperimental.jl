```
swap(t::AbstractTensor{Tuple{T1,T2}}) where {T1,T2} -> AbstractLinear{Tensor{Tuple{T2,T1}}}
swap(a::AbstractLinear{AbstractTensor{Tuple{T1,T2}})}) where {T1,T2}
    -> AbstractLinear{Tensor{Tuple{T1,T2}})}
```

この線形関数は、2成分テンソルの成分を入れ替えます。テンソル `t` の2つの成分が非ゼロの次数を持つ場合、通常の符号 `(-1)^(deg(t[1])*deg(t[2]))` が導入されます。デフォルトでは、すべての項は次数ゼロです。

`swap` は `regroup` の特別なケースであることに注意してください：これは単に `regroup(:((1, 2)), :((2, 1)))` として定義されています。

関連情報としては、[`Tensor`](@ref)、[`deg`](@ref)、[`regroup`](@ref)、[`LinearCombinations.DefaultCoefftype`](@ref)があります。

# 例

## 次数なしの例

```jldoctest swap
julia> t = Tensor("x", "z")
"x"⊗"z"

julia> swap(t)
Linear1{Tensor{Tuple{String, String}}, Int64} with 1 term:
"z"⊗"x"

julia> a = Linear("x" => 1, "yy" => 1) ⊗ Linear("z" => 1, "ww" => 1)
Linear{Tensor{Tuple{String, String}}, Int64} with 4 terms:
"x"⊗"ww"+"yy"⊗"ww"+"yy"⊗"z"+"x"⊗"z"

julia> swap(a)
Linear{Tensor{Tuple{String, String}}, Int64} with 4 terms:
"ww"⊗"x"+"z"⊗"yy"+"z"⊗"x"+"ww"⊗"yy"

julia> swap(a; coeff = 2)
Linear{Tensor{Tuple{String, String}}, Int64} with 4 terms:
2*"ww"⊗"x"+2*"z"⊗"yy"+2*"z"⊗"x"+2*"ww"⊗"yy"
```

## 次数ありの例

簡単のため、`String` の次数をその長さと定義します。

```jldoctest swap
julia> LinearCombinations.deg(x::String) = length(x)

julia> swap(t)   # 前と同じ t
Linear1{Tensor{Tuple{String, String}}, Int64} with 1 term:
-"z"⊗"x"

julia> swap(a)   # 前と同じ a
Linear{Tensor{Tuple{String, String}}, Int64} with 4 terms:
"ww"⊗"x"+"z"⊗"yy"-"z"⊗"x"+"ww"⊗"yy"
```
