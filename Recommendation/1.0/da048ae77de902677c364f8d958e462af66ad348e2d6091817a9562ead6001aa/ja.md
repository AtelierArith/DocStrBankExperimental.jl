```
generate(n_samples::Integer, n_items::Integer, features::AbstractVector{SyntheticFeature}, rules::AbstractVector{SyntheticRule}) -> DataAccessor
```

ランダムにサンプリングされた暗黙的フィードバックから合成データアクセサを生成します。各サンプルは異なるユーザーと見なされ、ユーザー属性は`SyntheticFeature`によって返される値に基づいて数値のワンホットエンコードされた特徴ベクトルで表されます。

このプロセスは、以下の論文のセクション7.3に基づいています：

  * M. Aharon, et al. **OFF-Set: One-pass Factorization of Feature Sets for Online Recommendation in Persistent Cold Start Settings**. [arXiv:1308.1792](https://arxiv.org/abs/1308.1792).

```julia
n_samples = 256
n_items = 5
data = generate(n_samples, n_items, features, rules)
```
