```
Categorical(p)
```

*カテゴリカル分布*は、確率ベクトル `p`（長さ `K`）によってパラメータ化されます。

$$
P(X = k) = p[k]  \quad \text{for } k = 1, 2, \ldots, K.
$$

```julia
Categorical(p)   # 確率ベクトル p を持つカテゴリカル分布
params(d)        # パラメータを取得、すなわち (p,)
probs(d)         # 確率ベクトルを取得、すなわち p
ncategories(d)   # カテゴリの数を取得、すなわち K
```

ここで、`p` は実数ベクトルでなければならず、すべての成分は非負であり、合計は1でなければなりません。

**注意:** 入力ベクトル `p` は、コピーされることなく構築された分布のフィールドとして直接使用されます。

`Categorical` は、`DiscreteNonParametric` 分布の特別なケースを説明する型エイリアスに過ぎないため、`DiscreteNonParametric` に対して定義された非専門的なメソッドは `Categorical` にも適用されます。

外部リンク:

  * [Wikipediaのカテゴリカル分布](http://en.wikipedia.org/wiki/Categorical_distribution)
