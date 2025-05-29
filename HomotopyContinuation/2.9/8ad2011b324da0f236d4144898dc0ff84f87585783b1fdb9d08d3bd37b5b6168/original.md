```
WeightedNorm(d::AbstractVector, norm::AbstractNorm; options...)
WeightedNorm(norm::AbstractNorm, n::Integer; options...)
WeightedNorm(norm::AbstractNorm, x::AbstractVector; options...)
```

A `WeightedNorm` represents a weighted variant of norm `norm` of a `n`-dimensional vector space.`A norm``||x||``is weighted by introducing a vector of additional weights`d`such that the new norm is``||D⁻¹x||``where``D``is the diagonal matrix with diagonal``d`. The `WeightedNorm` is desigened to change the weights dynamically by using [`init!(::WeightedNorm, x)`](@ref) and [`update!(::WeightedNorm, x)`](@ref). The weights are there constructed such that $||D⁻¹x|| ≈ 1.0$. The weights can be accessed and changed by indexing.

### Options

  * `scale_min = sqrt(eps())`: The minimal size of `dᵢ` is `scale_min` time the (weighted) norm of `x`.
  * `scale_abs_min = min(scale_min^2, 200 * sqrt(eps()))`: The absolute minimal size of `dᵢ`.
  * `scale_max = 1.0 / eps() / sqrt(2)`: The absolute maximal size of `dᵢ`
