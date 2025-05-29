```
vonmises(::AbstractSymmetricSecondOrderTensor{3})
```

フォン・ミーゼス応力を計算します。

$$
q = \sqrt{\frac{3}{2} \mathrm{dev}(\bm{\sigma}) : \mathrm{dev}(\bm{\sigma})} = \sqrt{3J_2}
$$

# 例

```jldoctest
julia> σ = rand(SymmetricSecondOrderTensor{3})
3×3 SymmetricSecondOrderTensor{3, Float64, 6}:
 0.325977  0.549051  0.218587
 0.549051  0.894245  0.353112
 0.218587  0.353112  0.394255

julia> vonmises(σ)
1.3078860814690232
```
