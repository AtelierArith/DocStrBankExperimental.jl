```
KroneckerSample(generator::AbstractVector, R::RandomizationMethod = NoRand()) <: DeterministicSamplingAlgorithm
```

クロンネッカー列は、ベクトルと方程式を使用して生成された点の集合です： `x[i] = i * generator .% 1`

ここで、`i` はサンプルサイズ `n` まで `1` から実行されます。この列は、`generator` の成分が有理数の体に対して線形独立である限り、等確率分布（無限の限界で均一）になります。

生成器が指定されていない場合、一般化された黄金比に基づく格子が使用されます。詳細については `GoldenSample` を参照してください。

クロンネッカー列は、理論が乏しいため、3次元を超える使用は推奨されません。`LatticeRuleSample` は、クロンネッカー列と似た振る舞いをするランク1の格子ルールを返しますが、より良い特性を持っています。

参考文献：Leobacher, G., & Pillichshammer, F. (2014). *Introduction to quasi-Monte Carlo integration and applications.* Switzerland: Springer International Publishing. https://link.springer.com/content/pdf/10.1007/978-3-319-03425-6.pdf
