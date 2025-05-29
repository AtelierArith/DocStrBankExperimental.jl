```
entropy_complexity_curves(c::StatisticalComplexity;
    num_max=1, num_min=1000) -> (min_entropy_complexity, max_entropy_complexity)
```

統計的複雑性に関する最大の複雑性-エントロピー曲線を計算します。これは、`num_max * total_outcomes(c.o)` の異なる正規化情報測度の値（最大複雑性曲線の場合）と、`num_min` の異なる正規化情報測度の値（最小複雑性曲線の場合）に基づいています。

この関数は、`c.hest` が例えば [`ShannonExtropy`](@ref) の場合、最大の「複雑性-エクストロピー曲線」を計算するためにも使用できます。これは、エントロピーの代わりにエクストロピーを使用した複雑性-エントロピー曲線の同等物です。

## 説明

統計的複雑性の設計方法により、特定の情報測度の値を持つデータに対して、最小および最大の可能な複雑性があります。最大複雑性曲線の計算時間は `O(total_outcomes(c.o)^2)` として成長し、結果の数が多い場合には非常に長くかかります。この関数は、S. Sippels の statcomp における実装 [Sippel2016](@cite) に触発されています。

この関数は、[`total_outcomes`](@ref) が事前に知られている任意の `ProbabilitiesEstimator` で機能します。
