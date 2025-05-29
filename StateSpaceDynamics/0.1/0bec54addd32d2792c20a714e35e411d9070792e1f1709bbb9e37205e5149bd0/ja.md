```
AutoRegressionEmission <: EmissionModel
```

自己回帰エミッションモデルを表す可変構造体で、`AutoRegression`モデルをラップします。

# フィールド

  * `inner_model::AutoRegression`: エミッションに使用される基盤となる自己回帰モデル。
