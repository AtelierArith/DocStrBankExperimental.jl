function proxy end

It's often useful to delegate methods like `logdensity` and `basemeasure` to those of a different measure. For example, a `Normal{(:μ,:σ)}` is equivalent to an affine transformation of a `Normal{()}`.

We *could* just have calls like `Normal(μ=2,σ=4)` directly construct a transformed measure, but this would make dispatch awkward.
