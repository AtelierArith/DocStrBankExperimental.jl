```
KMeans(k; rate=LearningRate(.6))
```

Approximate K-Means clustering of `k` clusters.

# Example

```
x = [randn() + 5i for i in rand(Bool, 10^6), j in 1:2]

o = fit!(KMeans(2, 2), eachrow(x))

sort!(o; rev=true)  # Order clusters by number of observations

classify(o, x[1])  # returns index of cluster closest to x[1]
```
