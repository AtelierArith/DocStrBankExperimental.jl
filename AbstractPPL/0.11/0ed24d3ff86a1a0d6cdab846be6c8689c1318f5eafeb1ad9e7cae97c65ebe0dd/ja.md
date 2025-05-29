```
condition(model, observations)
```

生成モデル `model` をいくつかの観測データに条件付けし、それらの（おそらく非正規化された）事後分布の新しいモデルを作成します。

`observations` は、サポートされている任意の内部トレースタイプ、または固定確率式である可能性があります。

不変条件 

```
m = decondition(condition(m, obs))
```

は、生成モデル `m` と任意の `obs` に対して成り立つべきです。
