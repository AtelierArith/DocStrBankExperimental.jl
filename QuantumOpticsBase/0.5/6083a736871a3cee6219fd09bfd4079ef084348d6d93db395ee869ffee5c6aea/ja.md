```
gaussianstate([T=ComplexF64,] b::PositionBasis, x0, p0, sigma)
gaussianstate([T=ComplexF64,] b::MomentumBasis, x0, p0, sigma)
```

`x0`と`p0`の周りに幅`sigma`のガウス状態を作成します。

実空間においてガウス状態は次のように定義されます。

$$
\Psi(x) = \frac{1}{\pi^{1/4}\sqrt{\sigma}}
            e^{i p_0 (x-\frac{x_0}{2}) - \frac{(x-x_0)^2}{2 \sigma^2}}
$$

これは運動量空間の定義に接続されています。

$$
\Psi(p) = \frac{\sqrt{\sigma}}{\pi^{1/4}}
            e^{-i x_0 (p-\frac{p_0}{2}) - \frac{1}{2}(p-p_0)^2 \sigma^2}
$$

フーリエ変換を介して

$$
\Psi(p) = \frac{1}{\sqrt{2\pi}}
            \int_{-\infty}^{\infty} e^{-ipx}\Psi(x) \mathrm{d}x
$$

この状態は次の特性を持ちます。

  * $$
    ⟨p⟩ = p_0
    $$
  * $$
    ⟨x⟩ = x_0
    $$
  * $$
    \mathrm{Var}(x) = \frac{σ^2}{2}
    $$
  * $$
    \mathrm{Var}(p) = \frac{1}{2 σ^2}
    $$

数値的に必要な離散化のために、追加のスケーリング因子$\sqrt{Δx}$と$\sqrt{Δp}$が使用され、$\langle x_i|Ψ\rangle = \sqrt{Δ x} Ψ(x_i)$および$\langle p_i|Ψ\rangle = \sqrt{Δ p} Ψ(p_i)$となり、結果として得られるKet状態が正規化されます。
