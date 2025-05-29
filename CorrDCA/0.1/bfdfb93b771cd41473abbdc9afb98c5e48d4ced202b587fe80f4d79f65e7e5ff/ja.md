```
compute_weights(Z::Matrix{Ti}, theta::Symbol) where Ti<:Integer
```

事前に計算された最適閾値のハミング距離 ≤ のシーケンスの数の正規化カウントを計算します。詳細については、`Fast and accurate multivariate Gaussian modeling of protein families: Predicting residue contacts and protein-interaction partners` [https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0092721] および特に補足情報のセクション `2 Reweighting Scheme` を参照してください。
