```
get_vector(M::AbstractProjectiveSpace, p, X, B::DefaultOrthonormalBasis{ℝ})
```

点 $p$ における接空間の基底 `B` における係数の一次元ベクトル $X$ を、[`AbstractProjectiveSpace`](@ref) $M=𝔽ℙ^n$ の点 $p$ における接ベクトル $Y$ に変換します。これは、$X$ を含む超平面の法線が $x$ 軸であるようにユニタリ変換し、法線が $p$ である超平面に変換します。

$$
q = p \overline{λ} + x
$$

とし、ここで $λ = \frac{⟨x, p⟩_{\mathrm{F}}}{|⟨x, p⟩_{\mathrm{F}}|}$、$⟨⋅, ⋅⟩_{\mathrm{F}}$ はフロベニウス内積を示し、$\overline{⋅}$ は複素数または四元数の共役を示します。$Y$ の公式は次の通りです。

$$
Y = \left(X - q\frac{2 \left\langle q, \begin{pmatrix}0 \\ X\end{pmatrix}\right\rangle_{\mathrm{F}}}{⟨q, q⟩_{\mathrm{F}}}\right) λ.
$$
