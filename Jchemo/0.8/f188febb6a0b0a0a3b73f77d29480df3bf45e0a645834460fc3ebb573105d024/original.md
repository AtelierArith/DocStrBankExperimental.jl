```
segmkf(n::Int, K::Int; rep = 1)
segmkf(group::Vector, K::Int; rep = 1)
```

Build segments of observations for K-fold cross-validation.  

  * `n` : Total nb. of observations in the dataset.    The sampling is implemented with 1:n.
  * `group` : A vector (n) defining blocks of observations.
  * `K` : Nb. folds (segments) splitting the `n` observations.

Keyword arguments:

  * `rep` : Nb. replications of the sampling.

For each replication, the function splits the `n` observations  to `K` segments  that can be used for K-fold cross-validation. 

If `group` is used (must be a vector of length `n`), the function  samples entire groups (= blocks) of observations instead of observations.  Such a block-sampling is required when data is structured by blocks and  when the response to predict is correlated within blocks.  This prevents underestimation of the generalization error.

The function returns a list (vector) of `rep` elements.  Each element of the list contains `K` segments (= `K` vectors). Each segment contains the indexes (position within 1:`n`) of  the sampled observations.    

## Examples

```julia
using Jchemo 

n = 10 ; K = 3
rep = 4 
segm = segmkf(n, K; rep)
i = 1 
segm[i]
segm[i][1]

n = 10 
group = ["A", "B", "C", "D", "E", "A", "B", "C", "D", "E"]    # blocks of the observations
tab(group) 
K = 3 ; rep = 4 
segm = segmkf(group, K; rep)
i = 1 
segm[i]
segm[i][1]
group[segm[i][1]]
group[segm[i][2]]
group[segm[i][3]]
```
