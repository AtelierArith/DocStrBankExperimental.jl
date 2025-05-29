```
get_vector(M::AbstractSphere{ℝ}, p, X, B::DefaultOrthonormalBasis)
```

点 `p` における [`AbstractSphere`](@ref) `M` の接空間の基底 `B` における係数の一次元ベクトル `X` を、`X` を含む超平面の法線が $x$ 軸である超平面から、法線が `p` である超平面に回転させることによって、点 `p` における接ベクトル `Y` に変換します。

$$
q = p λ + x
$$

とし、ここで $λ = \operatorname{sgn}(⟨x, p⟩)$、および $⟨⋅, ⋅⟩_{\mathrm{F}}$ はフロベニウス内積を示すとき、$Y$ の公式は次のようになります。

$$
Y = X - q\frac{2 \left\langle q, \begin{pmatrix}0 \\ X\end{pmatrix}\right\rangle_{\mathrm{F}}}{⟨q, q⟩_{\mathrm{F}}}.
$$
