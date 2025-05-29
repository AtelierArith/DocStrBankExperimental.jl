```
manifold_dimension(M::FixedRankMatrices)
```

`M`の次元が`m`x`n`でランクが`k`の`𝔽`-値の[`FixedRankMatrices`](@ref)に対する多様体次元を返します。すなわち、

$$
\dim(\mathcal M) = k(m + n - k) \dim_ℝ 𝔽,
$$

ここで、$\dim_ℝ 𝔽$は[`real_dimension`](@extref `ManifoldsBase.real_dimension-Tuple{ManifoldsBase.AbstractNumbers}`)の`𝔽`です。
