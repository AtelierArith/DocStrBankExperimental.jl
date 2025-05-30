```
noiseradius(x::AbstractVector, d::Int, τ, ρs, n = 1) → ρ
```

提案された*アルゴリズムを使用して[^Small2001]、[`PseudoPeriodic`](@ref)サロゲートの最適な`ρ`値を推定します。ここで、`ρs`は可能な`ρ`値のベクトルです。*論文は、正確に何を計算するかについてあいまいです。ここでは、`x`とそのサロゲートで同一の長さ2のペアが何回あるかを数えますが、**長さ3のペアの一部ではない**ものを数えます。

この関数は、これらのカウントと`ρ`に対する評価された分布のarg-maximumを直接返します。同じ引数を使用して`TimeseriesSurrogates._noiseradius`を使うと、実際の分布を取得できます。`n`は評価を`n`回繰り返すことを意味し、精度を向上させます。

[^Small2001]: Small et al., Surrogate test for pseudoperiodic time series data, [Physical Review Letters, 87(18)](https://doi.org/10.1103/PhysRevLett.87.188101)
