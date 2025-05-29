```
get_coordinates(M::AbstractSphere{ℝ}, p, X, B::DefaultOrthonormalBasis)
```

点 `p` における接ベクトル `X` を、[`AbstractSphere`](@ref) `M` の直交基底で表現するために、`X` を含む超平面を法線が $x$ 軸である超平面に回転させます。

$$
q = p λ + x
$$

とし、ここで $λ = \operatorname{sgn}(⟨x, p⟩)$、および $⟨⋅, ⋅⟩_{\mathrm{F}}$ はフロベニウス内積を示すとき、$Y$ の公式は次のようになります。

$$
\begin{pmatrix}0 \\ Y\end{pmatrix} = X - q\frac{2 ⟨q, X⟩_{\mathrm{F}}}{⟨q, q⟩_{\mathrm{F}}}.
$$
