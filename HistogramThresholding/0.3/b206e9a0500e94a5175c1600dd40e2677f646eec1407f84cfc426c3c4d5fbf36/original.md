```
t = find_threshold(histogram, edges, Yen())
t = find_threshold(img, Yen(); nbins = 256)
```

Computes the threshold value using Yen's maximum correlation criterion for bilevel thresholding.

# Output

Returns a real number `t` in `edges`. The `edges` parameter represents an `AbstractRange` which specifies the intervals associated with the histogram bins.

# Extended help

# Details

This algorithm uses the concept of *entropic correlation* of a gray level histogram to produce a threshold value.

Let $f_1, f_2, \ldots, f_I$ be the frequencies in the various bins of the histogram and $I$ the number of bins. With $N = \sum_{i=1}^{I}f_i$, let $p_i = \frac{f_i}{N}$ ($i = 1, \ldots, I$) denote the probability distribution of gray levels. From this distribution one derives two additional distributions. The first defined for discrete values $1$ to $s$ and the other, from $s+1$ to $I$. These distributions are

$$
A: \frac{p_1}{P_s}, \frac{p_2}{P_s}, \ldots, \frac{p_s}{P_s}
\quad \text{and} \quad
B: \frac{p_{s+1}}{1-P_s}, \ldots, \frac{p_n}{1-P_s}
\quad \text{where} \quad
P_s = \sum_{i=1}^{s}p_i.
$$

The entropic correlations associated with each distribution are

$$
C(A) = -\ln \sum_{i=1}^{s} \left( \frac{p_i}{P_s} \right)^2 \quad \text{and} \quad C(B) = -\ln \sum_{i=s+1}^{I} \left( \frac{p_i}{1 - P_s} \right)^2.
$$

Combining these two entropic correlation functions we have

$$
\psi(s) = -\ln \sum_{i=1}^{s} \left( \frac{p_i}{P_s} \right)^2 -\ln \sum_{i=s+1}^{I} \left( \frac{p_i}{1 - P_s} \right)^2.
$$

Finding the discrete value $s$ which maximises the function $\psi(s)$ produces the sought-after threshold value (i.e. the bin which determines the threshold).

# Arguments

The function arguments are described in more detail below.

## `histogram`

An `AbstractArray` storing the frequency distribution.

## `edges`

An `AbstractRange` specifying how the intervals for the frequency distribution are divided.

# Example

Compute the threshold for the "cameraman" image in the `TestImages` package.

```julia

using TestImages, ImageContrastAdjustment, HistogramThresholding

img = testimage("cameraman")
edges, counts = build_histogram(img, 256)
#=
  The `counts` array stores at index 0 the frequencies that were below the
  first bin edge. Since we are seeking a threshold over the interval
  partitioned by `edges` we need to discard the first bin in `counts`
  so that the dimensions of `edges` and `counts` match.
=#
t = find_threshold(counts[1:end], edges, Yen())
```

# Reference

1. Yen JC, Chang FJ, Chang S (1995), “A New Criterion for Automatic Multilevel Thresholding”, IEEE Trans. on Image Processing 4 (3): 370-378, [doi:10.1109/83.366472](https://doi.org/10.1109/83.366472)
