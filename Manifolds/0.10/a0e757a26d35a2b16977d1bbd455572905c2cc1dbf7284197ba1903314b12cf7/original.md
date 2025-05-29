```
exp(M::Hyperbolic, p, X)
```

Compute the exponential map on the [`Hyperbolic`](@ref) space $\mathcal H^n$ emanating from `p` towards `X`. The formula reads

$$
\exp_p X = \cosh(\sqrt{⟨X,X⟩_{\mathrm{M}}})p
+ \sinh(\sqrt{⟨X,X⟩_{\mathrm{M}}})\frac{X}{\sqrt{⟨X,X⟩_{\mathrm{M}}}},
$$

where $⟨⋅,⋅⟩_{\mathrm{M}}$ denotes the [`MinkowskiMetric`](@ref) on the embedding, the [`Lorentz`](@ref)ian manifold, see for example the extended version [BergmannPerschSteidl:2015:1](@cite) of the paper [BergmannPerschSteidl:2016:1](@cite).
