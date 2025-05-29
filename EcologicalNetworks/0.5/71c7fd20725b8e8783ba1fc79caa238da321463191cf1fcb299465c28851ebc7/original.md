```
information_decomposition(N::AbstractEcologicalNetwork; norm::Bool=false, dims=nothing)
```

Performs an information theory decomposition of a given ecological network, i.e. the information content in the normalized adjacency matrix is split in:

  * `:D` : difference in entropy of marginals compared to an uniform distribition
  * `:I` : mutual information
  * `:V` : variation of information / conditional entropy

If `norm=true`, the components are normalized such that their sum is equal to 1. One can optinally give the dimision, indicating whether to compute the indices for the rows (`dims=1`), columns (`dims=2`) or the whole matrix (default).

Result is returned in a Dict. Outputs in bits.

Stock, M.; Hoebeke, L.; De Baets, B. « Disentangling the Information in Species Interaction Networks ». Entropy 2021, 23, 703. https://doi.org/10.3390/e23060703
