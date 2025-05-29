```
decondition(conditioned_model)
```

`conditioned_model`から条件付け（すなわち、観測データ）を削除し、事前変数と観測変数に対する生成モデルに変換します。

不変式 

```
m == condition(decondition(m), obs)
```

は、条件付けされた変数 `obs` を持つモデル `m` に対して成り立つべきです。
