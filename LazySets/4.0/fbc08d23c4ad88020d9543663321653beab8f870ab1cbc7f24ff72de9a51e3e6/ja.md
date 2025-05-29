```
isbounded(eprojmap::ExponentialProjectionMap)
```

指数写像の射影が有界であるかどうかを確認します。

### 入力

  * `eprojmap` – 指数写像の射影

### 出力

`true` は、指数写像の射影が有界である場合。

### アルゴリズム

まず、左または右の射影行列がゼロであるか、またはラップされた集合が有界であるかを確認します。そうでない場合は、[`LazySets._isbounded_unit_dimensions`](@ref) を介して有界性を確認します。
