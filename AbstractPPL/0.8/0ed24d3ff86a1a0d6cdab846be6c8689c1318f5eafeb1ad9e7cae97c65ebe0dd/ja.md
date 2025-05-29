```
condition(model, observations)
```

生成モデル `model` をいくつかの観測データで条件付けし、それらに対する（おそらく非正規化された）事後分布の新しいモデルを作成します。

`observations` は、サポートされている任意の内部トレースタイプ、または固定された確率表現である可能性があります。

不変条件 

```
m = decondition(condition(m, obs))
```

は、生成モデル `m` と任意の `obs` に対して成り立つべきです。
