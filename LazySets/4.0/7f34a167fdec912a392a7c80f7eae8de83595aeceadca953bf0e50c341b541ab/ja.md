```
isbounded(ia::IntersectionArray)
```

有限数の集合の交差が有界であるかどうかを確認します。

### 入力

  * `ia` – 有限数の集合の交差

### 出力

交差が有界である場合は `true` を返します。

### アルゴリズム

まず、ラップされた集合のいずれかが有界であるかどうかを確認します。そうでない場合は、[`LazySets._isbounded_unit_dimensions`](@ref) を介して有界性を確認します。
