# 拡張ヘルプ

```
radius(X::LazySet, [p]::Real=Inf)
```

### アルゴリズム

デフォルトの実装は、`p == Inf` の場合に `ballinf_approximation` を使用して処理します。
