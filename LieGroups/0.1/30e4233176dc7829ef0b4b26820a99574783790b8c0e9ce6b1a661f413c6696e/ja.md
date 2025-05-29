```
compose(L::LieGroup{𝔽,RightSemidirectProductGroupOperation}, g, h)
```

半直積リー群 $L = G ⋊ H$ 上の群演算 $∘$ を計算します。すなわち、`g` $= (g_1,h_1)$、`h` $= (g_2,h_2)$ で、$g_1,g_2 ∈ G$、$h_1,h_2 ∈ H$ の場合、次のように計算します。

$$
    (g_1,h_1) ∘ (g_2,h_2) := (g_1 ⋄ σ_{h_1}(g_2), h_1 ⋆ h_2),
$$

ここで、$∘$ は $L$ 上の群演算を、$⋄$ と $⋆$ はそれぞれ $G$ と $H$ 上の群演算を示し、$σ$ は [`AbstractGroupActionType`](#ref) によって指定された群作用であり、[`RightSemidirectProductLieGroup`](@ref) $L$ 内で定義されています。
