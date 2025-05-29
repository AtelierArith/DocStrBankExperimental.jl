```
exp(M::Hyperbolic, p, X)
```

点 `p` から `X` へ向かう [`Hyperbolic`](@ref) 空間 $\mathcal H^n$ 上の指数写像を計算します。式は次のようになります。

$$
\exp_p X = \cosh(\sqrt{⟨X,X⟩_{\mathrm{M}}})p
+ \sinh(\sqrt{⟨X,X⟩_{\mathrm{M}}})\frac{X}{\sqrt{⟨X,X⟩_{\mathrm{M}}}},
$$

ここで $⟨⋅,⋅⟩_{\mathrm{M}}$ は埋め込み上の [`MinkowskiMetric`](@ref) を示し、[`Lorentz`](@ref) 多様体です。
