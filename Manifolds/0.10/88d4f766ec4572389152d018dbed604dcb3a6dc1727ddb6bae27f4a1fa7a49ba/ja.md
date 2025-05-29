```
inner(M::Hyperbolic, p, X, Y)
inner(M::Hyperbolic, p::HyperboloidPoint, X::HyperboloidTangentVector, Y::HyperboloidTangentVector)
```

ハイパーボロイドモデルにおける内積を計算します。すなわち、埋め込みにおける[`minkowski_metric`](@ref)です。式は次のようになります。

$$
g_p(X,Y) = ⟨X,Y⟩_{\mathrm{M}} = -X_{n}Y_{n} + \displaystyle\sum_{k=1}^{n-1} X_kY_k.
$$

これは埋め込みのメトリックを使用しています。[`Lorentz`](@ref)空間を参照してください。例えば、論文[BergmannPerschSteidl:2016:1](@cite)の拡張版[BergmannPerschSteidl:2015:1](@cite)を参照してください。 ```
