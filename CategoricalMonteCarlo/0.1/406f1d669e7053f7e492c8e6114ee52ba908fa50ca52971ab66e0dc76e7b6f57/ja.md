```
algorithm2_1_algorithm3_ratio(I::Vector{Int}, w::Vector{<:Real}, r::Real)
```

選択された `w` のコンポーネントをインデックスセット `I` によって正規化し、確率質量 `u = r / (1 + r)` を `w[I]` の中でゼロに等しい0個以上の要素に広げます。このとき、ゼロの要素の合計と非ゼロの要素の合計の比が `r` に等しくなるようにします。もし `w[I]` のすべての値がゼロであり、`r ≠ 0` の場合は、一様な確率質量のベクトルが返されます。`algorithm3_ratio!(algorithm2_1(I, w), u)` と同等ですが、より効率的です。

参照: [`algorithm2_1_algorithm3_ratio!`](@ref), [`algorithm2_1`](@ref),  [`algorithm3_ratio`](@ref)

# 例

```jldoctest
julia> I = [1, 2, 5, 6]; w = [10, 0, 30, 40, 0, 20]; r = 1.0;

julia> algorithm2_1_algorithm3_ratio(I, w, r)
4-element Vector{Float64}:
 0.16666666666666666
 0.25
 0.25
 0.3333333333333333

julia> algorithm3_ratio!(algorithm2_1(I, w), r)
4-element Vector{Float64}:
 0.16666666666666666
 0.25
 0.25
 0.3333333333333333
```
