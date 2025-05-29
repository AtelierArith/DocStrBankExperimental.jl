```
スプライン補間
```

これは[`interpolate`](@ref)によって返される型です。

`SplineInterpolation` `I`は、`I(x)`構文を使用して任意の点`x`で評価できます。

また、[`interpolate!`](@ref)を使用して、同じデータポイントに新しいデータで更新することもできます。

---

```
SplineInterpolation(undef, B::AbstractBSplineBasis, x::AbstractVector, [T = eltype(x)])
```

Bスプライン基底と補間（またはコレクション）点のセット`x`から`SplineInterpolation`を初期化します。

`x`の長さはBスプラインの数と等しくなければならないことに注意してください。

実際に`x`の位置で知られているデータを補間するには、[`interpolate!`](@ref)を使用します。
