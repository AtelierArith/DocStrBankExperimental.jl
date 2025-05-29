```
hamming_distribution(S, T)
```

Compute the distribution of pair-wise Hamming distances, which is defined as:

$$
c(k) := \sum_{\sigma\in S, \tau\in T} \delta({\rm dist}(\sigma, \tau), k)
$$

where $\delta$ is a function that returns 1 if two arguments are equivalent, 0 otherwise, ${\rm dist}$ is the Hamming distance function.

Returns the counting as a vector.
