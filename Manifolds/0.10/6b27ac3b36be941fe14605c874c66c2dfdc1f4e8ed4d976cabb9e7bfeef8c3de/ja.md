```
Circle{𝔽} <: AbstractManifold{𝔽}
```

円 $𝕊^1$ は、ここでは $[-π,π)$ の実値点または絶対値 $\lvert z\rvert = 1$ の複素値点 $z ∈ ℂ$ で表される多様体です。

# コンストラクタ

```
Circle(𝔽=ℝ)
```

角度で表される `ℝ`-値の円を生成します。これは、[`AbstractNumbers`](@extref ManifoldsBase number-system) `𝔽=ℂ` を使用するように設定することで、単位数の `ℂ`-値の円を得ることもできます。
