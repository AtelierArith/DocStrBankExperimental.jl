```
compose(L::LieGroup{𝔽,LeftSemidirectProductGroupOperation}, g, h)
```

Compute the group operation $∘$ on the semidirect product Lie group $L = G ⋉ H$, that is for `g` $= (g_1,h_1)$, `h` $= (g_2,h_2)$ with $g_1,g_2 ∈ G$, $h_1,h_2 ∈ H$ this computes

$$
    (g_1,h_1) ∘ (g_2,h_2) := (g_1 ⋄ g_2, h_1 ⋆ σ_{g_1}(h_2)).
$$

where $∘$ denotes the group operation on $L$, $⋄$ and $⋆$ those on $G$ and $H$, respectively, and $σ$ is the group action specified by the [`AbstractGroupActionType`](#ref) within the [`LeftSemidirectProductLieGroup`](@ref)  $L$.
