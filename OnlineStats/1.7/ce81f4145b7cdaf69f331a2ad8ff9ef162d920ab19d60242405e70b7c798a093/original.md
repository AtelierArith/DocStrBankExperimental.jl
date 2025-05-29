```
FastTree(p::Int, nclasses=2; stat=FitNormal(), maxsize=5000, splitsize=1000)
```

Calculate a decision tree of `p` predictors variables and classes `1, 2, …, nclasses`. Nodes split when they reach `splitsize` observations until `maxsize` nodes are in the tree. Each variable is summarized by `stat`, which can be `FitNormal()` or `Hist(nbins)`.

# Example

```
x = randn(10^5, 10)
y = rand([1,2], 10^5)

o = fit!(FastTree(10), zip(eachrow(x),y))

xi = randn(10)
classify(o, xi)
```
