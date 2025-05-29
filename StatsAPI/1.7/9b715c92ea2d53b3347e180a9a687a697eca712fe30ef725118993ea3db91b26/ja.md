```
crossmodelmatrix(model::RegressionModel)
```

`X'X`を返します。ここで、`X`は`model`のモデル行列です。この関数は、可能であれば`model`に保存されている事前計算された行列を返します。
