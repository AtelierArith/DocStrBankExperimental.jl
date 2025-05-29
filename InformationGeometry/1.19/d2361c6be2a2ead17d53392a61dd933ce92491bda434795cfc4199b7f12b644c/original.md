```
GeneralizedDataSet(dist::ContinuousMultivariateDistribution, dims::Tuple{Int,Int,Int}=(length(dist), 1, 1))
```

Data structure which can take general x-y-covariance into account where `dims=(Npoints, xdim, ydim)` indicates the dimensionality of the data. `dist` should constitute a smooth distribution over the space $\mathcal{X}^N \times \mathcal{Y}^N$ where `mean(dist)` is interpreted as the concatenation of the (most likely values for the) observations $(x_1, ..., x_N, y_1, ..., y_N)$ and the width of `dist` specifies the uncertainty in the signal. Typically, `dist` is a multivariate Gaussian but other distributions such as Cauchy or student's t-distributions are also possible. Thus, arbitrary correlations between the dependent $y$ and independent $x$ variables can be encoded.

!!! note
    If there is no correlation between the $x$ and $y$ variables (i.e. if the offdiagonal blocks of `cov(dist)` are zero), it can be more performant to use the type `DataSetExact` to encode the given data instead.

