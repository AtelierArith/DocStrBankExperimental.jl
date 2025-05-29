```
get_coordinates(M::AbstractProjectiveSpace, p, X, B::DefaultOrthonormalBasis{ℝ})
```

点 $p$ における接ベクトル $X$ を、法線が $p$ である $X$ を含む超平面を、法線が $x$ 軸である超平面にユニタリ変換することによって、[`AbstractProjectiveSpace`](@ref) $M = 𝔽ℙ^n$ の直交基底で表現します。

$$
q = p \overline{λ} + x
$$

とし、ここで $λ = \frac{⟨x, p⟩_{\mathrm{F}}}{|⟨x, p⟩_{\mathrm{F}}|}$、$⟨⋅, ⋅⟩_{\mathrm{F}}$ はフロベニウス内積を示し、$\overline{⋅}$ は複素数または四元数の共役を示します。このとき、$Y$ の式は次のようになります。

$$
\begin{pmatrix}0 \\ Y\end{pmatrix} = \left(X - q\frac{2 ⟨q, X⟩_{\mathrm{F}}}{⟨q, q⟩_{\mathrm{F}}}\right)\overline{λ}.
$$
