```
RSADA{D,S}
```

A R-SADA monitoring statistic, whcih is used for monitoring the mean of partially-observed independent data streams. The monitoring statistic iteratively samples arms (data streams) and updates a set of local statistics based on the observed values of the data streams. The RSADA algorithm uses the local statistics to make decisions on which arms to sample at each iteration.

# Fields

  * `k`: The allowance constant of the CUSUM Control chart. Default value is 0.1.
  * `mu_min`: The minimum value of the mean shift to detect. Default value is 0.2.
  * `p::Int`: The number of independent data streams. Default value is 1.
  * `q::Int`: The number of data streams that are observable at each iteration. Default value is 1.
  * `dist::Distribution`: The distribution of the data streams. Default value is `Normal(0,1)`.
  * `value`: The current value of the monitoring statistic. Default value is 0.0.
  * `eta`: The vector of augmented variables. Initialized to be a vector of zeros for each data stream.
  * `obs::Vector{Int}`: The indices of the data streams to sample. Default value is an array of q random integers between 1 and p.
  * `S1::Vector{F}`: The sum of the rewards for each arm.
  * `S2::Vector{F}`: The sum of the squared rewards for each arm.

# References

Xian, X., Zhang, C., Bonk, S., & Liu, K. (2019). Online monitoring of big data streams: A rank-based sampling algorithm by data augmentation. Journal of Quality Technology, 53(2), 135-153. https://doi.org/10.1080/00224065.2019.1681924
