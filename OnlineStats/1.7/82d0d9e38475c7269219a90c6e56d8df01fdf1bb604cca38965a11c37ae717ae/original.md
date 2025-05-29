```
NBClassifier(p::Int, T::Type; stat = Hist(15))
```

Calculate a naive bayes classifier for classes of type `T` and `p` predictors.  For each class `K`, predictor variables are summarized by the `stat`.

# Example

```
x, y = randn(10^4, 10), rand(Bool, 10^4)

o = fit!(NBClassifier(10, Bool), zip(eachrow(x),y))
collect(keys(o))
probs(o)

xi = randn(10)
predict(o, xi)
classify(o, xi)
```
