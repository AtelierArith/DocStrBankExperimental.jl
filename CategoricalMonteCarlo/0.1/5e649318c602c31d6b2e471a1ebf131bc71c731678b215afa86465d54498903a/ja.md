```
algorithm2_1_algorithm3(I::Vector{Int}, w::Vector{<:Real}, u::Real)
```

選択された `w` のコンポーネントをインデックスセット `I` によって正規化し、確率質量 `0 ≤ u ≤ 1` をゼロに等しい0個以上の要素に広げることで、確率のベクトルを返します。もし `w[I]` のすべての値がゼロであり、かつ `u ≠ 0` の場合、均一な確率質量のベクトルが返されます。`algorithm3!(algorithm2_1(I, w), u)` と同等ですが、より効率的です。

参照: [`algorithm2_1_algorithm3!`](@ref), [`algorithm2_1`](@ref), [`algorithm3`](@ref)

# 例

```jldoctest
julia> I = [1, 2, 5, 6]; w = [10, 0, 30, 40, 0, 20]; u = 0.5;

julia> algorithm2_1_algorithm3(I, w, u)
4-element Vector{Float64}:
 0.16666666666666666
 0.25
 0.25
 0.3333333333333333

julia> algorithm3!(algorithm2_1(I, w), u)
4-element Vector{Float64}:
 0.16666666666666666
 0.25
 0.25
 0.3333333333333333
```
