```
RateVariationAcrossSites(; pinv=0.0, alpha=Inf, ncat=4)
```

サイト間（または特性間）の変数置換率のモデルで、離散ガンマモデル（+G、Yang 1994、Journal of Molecular Evolution）または不変サイトモデル（+I、Hasegawa、Kishino & Yano 1985 J Mol Evol）を使用します。両方のタイプの率の変動を組み合わせることができます（+G+I、Gu、Fu & Li 1995、Mol Biol Evol）が、これは推奨されません（Jia、Lo & Ho 2014 PLOS One）。率の変動を使用すると、パラメータの数が1つ（+Gまたは+I）または2つ（+G+I）増加します。

望ましい分布または率の平均が1であるため、不変サイトがない場合は形状αおよびスケールθ=1/α（率β=α）のガンマ分布を使用し、不変サイトの割合pinvがある場合はスケールθ=1/(α(1-pinv))、すなわち率β=α(1-pinv)を使用します。形状パラメータはここでalphaと呼ばれます。ガンマ分布は`ncat`カテゴリに離散化されます。各カテゴリでは、カテゴリの率の乗数はガンマ分布の正規化された分位点です。

```jldoctest
julia> rv = RateVariationAcrossSites()
Rate variation across sites: discretized Gamma
categories for Gamma discretization: 1
rates: [1.0]

julia> nparams(rv)
0

julia> typeof(rv)
PhyloTraits.RVASGamma{1}

julia> rv = RateVariationAcrossSites(alpha=1.0, ncat=4)
Rate variation across sites: discretized Gamma
alpha: 1.0
categories for Gamma discretization: 4
rates: [0.146, 0.513, 1.071, 2.27]

julia> typeof(rv)
PhyloTraits.RVASGamma{4}

julia> PhyloTraits.setalpha!(rv, 2.0)
Rate variation across sites: discretized Gamma
alpha: 2.0
categories for Gamma discretization: 4
rates: [0.319, 0.683, 1.109, 1.889]

julia> nparams(rv)
1

julia> rv = RateVariationAcrossSites(pinv=0.3)
Rate variation across sites: +I (invariable sites)
pinv: 0.3
rates: [0.0, 1.429]

julia> nparams(rv)
1

julia> typeof(rv)
PhyloTraits.RVASInv

julia> PhyloTraits.setpinv!(rv, 0.05)
Rate variation across sites: +I (invariable sites)
pinv: 0.05
rates: [0.0, 1.053]

julia> rv = RateVariationAcrossSites(pinv=0.3, alpha=2.0, ncat=4)
Rate variation across sites: discretized Gamma+I
pinv: 0.3
alpha: 2.0
categories for Gamma discretization: 4
rates: [0.0, 0.456, 0.976, 1.584, 2.698]
probabilities: [0.3, 0.175, 0.175, 0.175, 0.175]

julia> nparams(rv)
2

julia> typeof(rv)
PhyloTraits.RVASGammaInv{5}

julia> PhyloTraits.setalpha!(rv, 3.0)
Rate variation across sites: discretized Gamma+I
pinv: 0.3
alpha: 3.0
categories for Gamma discretization: 4
rates: [0.0, 0.6, 1.077, 1.584, 2.454]
probabilities: [0.3, 0.175, 0.175, 0.175, 0.175]

julia> PhyloTraits.setpinv!(rv, 0.05)
Rate variation across sites: discretized Gamma+I
pinv: 0.05
alpha: 3.0
categories for Gamma discretization: 4
rates: [0.0, 0.442, 0.793, 1.167, 1.808]
probabilities: [0.05, 0.238, 0.238, 0.238, 0.238]

julia> PhyloTraits.setpinvalpha!(rv, 0.1, 5.0)
Rate variation across sites: discretized Gamma+I
pinv: 0.1
alpha: 5.0
categories for Gamma discretization: 4
rates: [0.0, 0.593, 0.91, 1.221, 1.721]
probabilities: [0.1, 0.225, 0.225, 0.225, 0.225]
```
