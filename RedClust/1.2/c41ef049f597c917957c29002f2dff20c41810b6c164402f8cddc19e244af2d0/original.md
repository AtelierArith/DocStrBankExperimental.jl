```
infodist(a::ClustLabelVector, b::ClustLabelVector;
normalised = true) -> Float64
```

Computes the information distance between two clusterings. The information distance is defined as

$$
d_{\mathrm{ID}}(a, b) = \max \{H(A), H(B)\} - I(A, B)
$$

where $A$ and $B$ are the cluster membership probability functions for $a$ and $b$ respectively, $H$ denotes the entropy of a distribution, and $I$ denotes the mutual information between two distributions. The information distance has range $[0, \log N]$ where $N$ is the number of observations. If normalised = true, the result is scaled to the range $[0, 1]$.
