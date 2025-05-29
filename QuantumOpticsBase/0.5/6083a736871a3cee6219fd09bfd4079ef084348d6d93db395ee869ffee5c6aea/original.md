```
gaussianstate([T=ComplexF64,] b::PositionBasis, x0, p0, sigma)
gaussianstate([T=ComplexF64,] b::MomentumBasis, x0, p0, sigma)
```

Create a Gaussian state around `x0` and`p0` with width `sigma`.

In real space the gaussian state is defined as

$$
\Psi(x) = \frac{1}{\pi^{1/4}\sqrt{\sigma}}
            e^{i p_0 (x-\frac{x_0}{2}) - \frac{(x-x_0)^2}{2 \sigma^2}}
$$

and is connected to the momentum space definition

$$
\Psi(p) = \frac{\sqrt{\sigma}}{\pi^{1/4}}
            e^{-i x_0 (p-\frac{p_0}{2}) - \frac{1}{2}(p-p_0)^2 \sigma^2}
$$

via a Fourier-transformation

$$
\Psi(p) = \frac{1}{\sqrt{2\pi}}
            \int_{-\infty}^{\infty} e^{-ipx}\Psi(x) \mathrm{d}x
$$

The state has the properties

  * $⟨p⟩ = p_0$
  * $⟨x⟩ = x_0$
  * $\mathrm{Var}(x) = \frac{σ^2}{2}$
  * $\mathrm{Var}(p) = \frac{1}{2 σ^2}$

Due to the numerically necessary discretization additional scaling factors $\sqrt{Δx}$ and $\sqrt{Δp}$ are used so that $\langle x_i|Ψ\rangle = \sqrt{Δ x} Ψ(x_i)$ and $\langle p_i|Ψ\rangle = \sqrt{Δ p} Ψ(p_i)$ so that the resulting Ket state is normalized.
