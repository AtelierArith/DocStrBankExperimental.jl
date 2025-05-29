```
inv(SDPG::LieGroup{𝔽,Op,M}, g) where {𝔽,Op<:SemiDirectProductGroupOperation,M<:ProductManifold}
```

要素 $g = (g_1, g_2)$ の逆要素を計算します。

$$
g^{-1} = (g_1^{-1}, σ_{g_1^{-1}}g_2).
$$

左のバリアントの場合と、

$$
g^{-1} = (σ_{g_2^{-1}} g_1, g_2^{-1})
$$

右のバリアントの場合、それぞれです。詳細は [HilgertNeeb:2012; Proof of Lemma 2.2.3](@cite) を参照してください。
