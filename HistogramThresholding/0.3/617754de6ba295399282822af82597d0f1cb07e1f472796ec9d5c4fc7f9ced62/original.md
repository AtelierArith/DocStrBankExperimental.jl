```
t = find_threshold(histogram, edges, Otsu())
t = find_threshold(img, Otsu(); nbins = 256)
```

Under the assumption that the histogram is bimodal the threshold is set so that the resultant between-class variance is maximal.

# Output

Returns a real number `t` in `edges`. The `edges` parameter represents an `AbstractRange` which specifies the intervals associated with the histogram bins.

# Extended help

# Details

Let $f_i$ $(i=1 \ldots I)$ denote the number of observations in the $i$th bin of the histogram. Then the probability that an observation belongs to the $i$th bin is given by  $p_i = \frac{f_i}{N}$ ($i = 1, \ldots, I$), where $N = \sum_{i=1}^{I}f_i$.

The choice of a threshold $T$ partitions the data into two categories, $C_0$ and $C_1$. Let

$$
P_0(T) = \sum_{i = 1}^T p_i \quad \text{and} \quad P_1(T) = \sum_{i = T+1}^I p_i
$$

denote the cumulative probabilities,

$$
\mu_0(T) = \sum_{i = 1}^T i \frac{p_i}{P_0(T)} \quad \text{and} \quad \mu_1(T) = \sum_{i = T+1}^I i \frac{p_i}{P_1(T)}
$$

denote the means, and

$$
\sigma_0^2(T) = \sum_{i = 1}^T (i-\mu_0(T))^2 \frac{p_i}{P_0(T)} \quad \text{and} \quad \sigma_1^2(T) = \sum_{i = T+1}^I (i-\mu_1(T))^2 \frac{p_i}{P_1(T)}
$$

denote the variances of categories $C_0$ and $C_1$, respectively. Furthermore, let

$$
\mu = P_0(T)\mu_0(T) + P_1(T)\mu_1(T),
$$

represent the overall mean,

$$
\sigma_b^2(T) = P_0(T)(\mu_0(T) - \mu)^2 + P_1(T)(\mu_1(T) - \mu)^2,
$$

the between-category variance, and

$$
\sigma_w^2(T) = P_0(T) \sigma_0^2(T) +  P_1(T)\sigma_1^2(T)
$$

the within-category variance, respectively.

Finding the discrete value $T$ which maximises the function $\sigma_b^2(T)$ produces the sought-after threshold value (i.e. the bin which determines the threshold). As it turns out, that threshold value is equal to the threshold decided by minimizing the within-category variances criterion $\sigma_w^2(T)$. Furthermore, that threshold is also the same as the threshold calculated by maximizing the ratio of between-category variance to within-category variance.

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
edges, counts = build_histogram(img,256)
#=
  The `counts` array stores at index 0 the frequencies that were below the
  first bin edge. Since we are seeking a threshold over the interval
  partitioned by `edges` we need to discard the first bin in `counts`
  so that the dimensions of `edges` and `counts` match.
=#
t = find_threshold(counts[1:end], edges, Otsu())
```

# Reference

1. Nobuyuki Otsu (1979). “A threshold selection method from gray-level histograms”. *IEEE Trans. Sys., Man., Cyber.* 9 (1): 62–66. [doi:10.1109/TSMC.1979.4310076](http://dx.doi.org/doi:10.1109/TSMC.1979.4310076)
