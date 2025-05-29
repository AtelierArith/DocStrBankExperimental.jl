```
NBClassifier(p::Int, T::Type; stat = Hist(15))
```

クラス `T` のためのナイーブベイズ分類器を `p` 個の予測子で計算します。各クラス `K` に対して、予測変数は `stat` によって要約されます。

# 例

```
x, y = randn(10^4, 10), rand(Bool, 10^4)

o = fit!(NBClassifier(10, Bool), zip(eachrow(x),y))
collect(keys(o))
probs(o)

xi = randn(10)
predict(o, xi)
classify(o, xi)
```
