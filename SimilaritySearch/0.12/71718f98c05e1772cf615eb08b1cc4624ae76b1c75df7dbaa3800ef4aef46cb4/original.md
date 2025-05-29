```
distsample(dist::SemiMetric, X::AbstractDatabase; samplesize=sqrt(|X|))

Computes a sample of the pairwise distance matrix. 
Returns anarray of size `samplesize`

- `dist`: Distance function
- `X`: input database
- `samplesize`: the size of the sample
```
