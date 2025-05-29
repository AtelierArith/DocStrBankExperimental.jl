```
cronbachalpha(covmatrix::AbstractMatrix{<:Real})
```

Calculate Cronbach's alpha (1951) from a covariance matrix `covmatrix` according to the [formula](https://en.wikipedia.org/wiki/Cronbach%27s_alpha):

$$
\rho = \frac{k}{k-1} (1 - \frac{\sum^k_{i=1} \sigma^2_i}{\sum_{i=1}^k \sum_{j=1}^k \sigma_{ij}})
$$

where $k$ is the number of items, i.e. columns, $\sigma_i^2$ the item variance, and $\sigma_{ij}$ the inter-item covariance.

Returns a `CronbachAlpha` object that holds:

  * `alpha`: the Cronbach's alpha score for all items, i.e. columns, in `covmatrix`; and
  * `dropped`: a vector giving Cronbach's alpha scores if a specific item, i.e. column, is dropped from `covmatrix`.

# Example

```jldoctest
julia> using StatsBase

julia> cov_X = [10 6 6 6;
                6 11 6 6;
                6 6 12 6;
                6 6 6 13];

julia> cronbachalpha(cov_X)
Cronbach's alpha for all items: 0.8136

Cronbach's alpha if an item is dropped:
item 1: 0.7500
item 2: 0.7606
item 3: 0.7714
item 4: 0.7826
```
