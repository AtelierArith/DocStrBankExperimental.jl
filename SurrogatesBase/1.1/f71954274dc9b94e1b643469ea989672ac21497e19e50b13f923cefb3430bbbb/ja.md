```
finite_posterior(s::AbstractStochasticSurrogate, xs::AbstractVector)
```

点 `xs` における事後分布を返します。

`AbstractStochasticSurrogate` は、返されるオブジェクトに対して以下のいくつかまたはすべてのメソッドを実装することがあります：

  * `mean(finite_posterior(s,xs))` は `xs` における事後平均の `Vector` を返します
  * `var(finite_posterior(s,xs))` は `xs` における事後分散の `Vector` を返します
  * `mean_and_var(finite_posterior(s,xs))` は `xs` における事後平均の `Vector` と事後分散の `Vector` からなる `Tuple` を返します
  * `rand(finite_posterior(s,xs))` は、点 `xs` における結合事後からのサンプルである `Vector` を返します

`X` が行列である場合は `mean(finite_posterior(s, eachslice(X, dims = 2)))` を使用してください。
