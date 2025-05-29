```
RateVariationAcrossSites(; pinv=0.0, alpha=Inf, ncat=4)
```

Model for variable substitution rates across sites (or across traits) using the discrete Gamma model (+G, Yang 1994, Journal of Molecular Evolution) or the invariable-sites model (+I, Hasegawa, Kishino & Yano 1985 J Mol Evol). Both types of rate variation can be combined (+G+I, Gu, Fu & Li 1995, Mol Biol Evol) but this is discouraged (Jia, Lo & Ho 2014 PLOS One). Using rate variation increases the number of parameters by one (+G or +I) or by two (+G+I).

Because the mean of the desired distribution or rates is 1, we use a Gamma distribution with shape α and scale θ=1/α (rate β=α) if no invariable sites, or scale θ=1/(α(1-pinv)), that is rate β=α(1-pinv) with a proportion pinv of invariable sites. The shape parameter is referred to as alpha here. The Gamma distribution is discretized into `ncat` categories. In each category, the category's rate multiplier is a normalized quantile of the gamma distribution.

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
