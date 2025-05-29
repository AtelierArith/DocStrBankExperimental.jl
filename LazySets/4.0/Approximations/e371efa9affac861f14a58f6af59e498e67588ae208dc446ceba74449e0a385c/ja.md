```
underapproximate(X::LazySet, ::Type{<:Ball2})
```

集合 `X` に内接する最大のユークリッド球を計算します。

### 入力

  * `X`     – 集合
  * `Ball2` – 目標タイプ

### 出力

`X` に含まれる最大の `Ball2`。

### アルゴリズム

`chebyshev_center_radius(X)` を使用します。
