```
relative_entropy([base=2,] p::AbstractVector, q::AbstractVector)
```

Computes the relative entropy D(`p`||`q`) = Σᵢpᵢlog(pᵢ/qᵢ) between two non-negative vectors `p` and `q` using a base `base` logarithm. Note that the support of `p` must be contained in the support of `q` but for efficiency this is not checked.

Reference: [Relative entropy](https://en.wikipedia.org/wiki/Relative_entropy)
