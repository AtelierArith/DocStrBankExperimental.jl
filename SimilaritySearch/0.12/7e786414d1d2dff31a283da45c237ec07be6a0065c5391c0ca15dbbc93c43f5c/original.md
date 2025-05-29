```
distsample_ut(dist::SemiMetric, X::AbstractDatabase; prob=0.01, samplesize=0)
distsample(dist::SemiMetric, X::AbstractDatabase; prob=0.01, samplesize=sqrt(|X|))

Computes a sample of the upper triangular pairwise distance matrix. 
Returns an array of distances of close to ``prob * n^2/2`` entries for a database of size ``n``.
This method is fine to work in small datasets (not million sized datasets); this method do not return duplicates nor symmetric duplicates

- `dist`: Distance function
- `X`: input database
- `prob`: sampling probability (on the upper triangle pairwise distance matrix)
- `samplesize`: if samplesize is given, the it ignores the given probability and computes the necessary `prob` to achieve a value close to `samplesize`
```
