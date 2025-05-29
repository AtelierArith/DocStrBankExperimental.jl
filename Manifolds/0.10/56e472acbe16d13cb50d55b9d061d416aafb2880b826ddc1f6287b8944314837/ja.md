```
log(M::AbstractProjectiveSpace, p, q)
```

[`AbstractProjectiveSpace`](@ref) `M`$= 𝔽ℙ^n$ 上の対数写像を計算します。すなわち、点 `p` から出発し、時間 1 で `M` 上の `q` に到達する対応する [`geodesic`](@extref `ManifoldsBase.geodesic-Tuple{AbstractManifold, Any, Any}`) の接ベクトルです。式は次のようになります。

$$
\log_p q = (q λ - \cos θ p) \frac{θ}{\sin θ},
$$

ここで、$θ = \arccos|⟨q, p⟩_{\mathrm{F}}|$ は $p$ と $q$ の間の [`distance`](@ref distance(::AbstractProjectiveSpace, p, q)) であり、$⟨⋅, ⋅⟩_{\mathrm{F}}$ はフロベニウス内積、$λ = \frac{⟨q, p⟩_{\mathrm{F}}}{|⟨q, p⟩_{\mathrm{F}}|} ∈ 𝔽$ は $d_{𝔽^{n+1}}(p - q λ)$ を最小化する単位スカラーです。つまり、$q λ$ は埋め込みにおいて $p$ に最も近い同値類 $[q]$ のメンバーです。その結果、$\exp_p \circ \log_p \colon q ↦ q λ$ となります。

実数の [`AbstractSphere`](@ref) $𝕊^n$ と実射影空間 $ℝℙ^n$ の対数写像は、$p$ と $q$ が同じ半球にあるときに同一です。 ```
