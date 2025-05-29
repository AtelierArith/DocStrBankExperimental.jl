```
isbounded(cap::Intersection)
```

二つの集合の交差が有界であるかどうかを確認します。

### 入力

  * `cap` – 二つの集合の交差

### 出力

交差が有界であれば `true`。

### アルゴリズム

まず、ラップされた集合のいずれかが有界であるかどうかを確認します。そうでなければ、[`LazySets._isbounded_unit_dimensions`](@ref) を介して有界性を確認します。
