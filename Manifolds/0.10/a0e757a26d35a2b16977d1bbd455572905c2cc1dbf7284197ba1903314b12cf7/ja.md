```
exp(M::Hyperbolic, p, X)
```

点 `p` から `X` へ向かう [`Hyperbolic`](@ref) 空間 $\mathcal H^n$ 上の指数写像を計算します。式は次のようになります。

$$
\exp_p X = \cosh(\sqrt{⟨X,X⟩_{\mathrm{M}}})p
+ \sinh(\sqrt{⟨X,X⟩_{\mathrm{M}}})\frac{X}{\sqrt{⟨X,X⟩_{\mathrm{M}}}},
$$

ここで $⟨⋅,⋅⟩_{\mathrm{M}}$ は埋め込み上の [`MinkowskiMetric`](@ref) を示し、[`Lorentz`](@ref) 多様体に関するもので、例えば論文 [BergmannPerschSteidl:2016:1](@cite) の拡張版 [BergmannPerschSteidl:2015:1](@cite) を参照してください。
