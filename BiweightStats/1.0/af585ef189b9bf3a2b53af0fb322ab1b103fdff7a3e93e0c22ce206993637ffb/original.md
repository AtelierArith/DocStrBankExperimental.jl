```
BiweightStats
```

A module for robust statistics based on the biweight transform.[^1]

# Biweight Statistics

The basis of the biweight transform is robust analysis, that is, statistics which are resilient to outliers while still efficiently representing a variety of underlying distributions. The biweight transform is based off the *median* and the *median absolute deviation (MAD)*. The median is a robust estimator of location, and the MAD is a robust estimator of scale

$$
\mathrm{MAD}(X) = \mathrm{median}\left|X_i - \bar{X}\right|
$$

where $\bar{X}$ is the median.

The biweight transform improves upon these estimates by filtering out data beyond a critical cutoff. The analogy is doing a sigma-filter, but using these robust statistics instead of the standard deviation and mean.

$$
u_i = \frac{X_i - \bar{X}}{c \cdot \mathrm{MAD}}
$$

$$
\forall i \quad\mathrm{where}\quad u_i^2 \le 1
$$

The cutoff factor, $c$, can be directly related to a Gaussian standard-deviation by multiplying by 1.4826[^2]. So a typical value of $c=9$ means outliers further than $13.3\sigma$ are clipped (for residuals which are truly Gaussian-distributed). In addition, in `BiweightStats`, we also skip `NaN`s and `Inf`s (but not `missing` or `nothing`).

# References

[^1]: [NIST: biweight](https://www.itl.nist.gov/div898/software/dataplot/refman2/ch2/biweight.pdf)

[^2]: [Median absolute deviation](https://en.wikipedia.org/wiki/Median_absolute_deviation#Relation_to_standard_deviation)

# Methods

  * [`location`](@ref)
  * [`scale`](@ref)
  * [`midvar`](@ref)
  * [`midcov`](@ref)
  * [`midcor`](@ref)
