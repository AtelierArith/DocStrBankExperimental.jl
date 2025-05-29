```
inv(SDPG::LieGroup{𝔽,Op,M}, g) where {𝔽,Op<:SemiDirectProductGroupOperation,M<:ProductManifold}
```

Compute the inverse element of an element $g = (g_1, g_2)$ given by

$$
g^{-1} = (g_1^{-1}, σ_{g_1^{-1}}g_2).
$$

for the left variant and

$$
g^{-1} = (σ_{g_2^{-1}} g_1, g_2^{-1})
$$

for the right variant, respectively. See also [HilgertNeeb:2012; Proof of Lemma 2.2.3](@cite).
