# 拡張ヘルプ

```
rectify(X::LazySet, [concrete_intersection]::Bool=false)
```

### アルゴリズム

`X` が正と負の両方である各次元について、`X` をこれらの2つの部分に分割し、負の部分をゼロに投影します。
