```
sample(d::TruncatedMVNormal, n::Integer, max_iter::Integer=10000)
```

Sample `n` samples from the distribution `d`.

Returns an D x n `Matrix` of samples where D is the dimension of the distribution `d`.
