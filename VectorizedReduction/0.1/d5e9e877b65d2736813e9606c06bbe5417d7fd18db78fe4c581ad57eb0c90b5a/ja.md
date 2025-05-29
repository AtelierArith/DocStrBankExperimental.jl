```
vtmaximum(f, A::AbstractArray, dims=:)
```

与えられた `dims` に対して、`A` の各要素に `f` を適用して最大値を計算します。

# 警告

`NaN` 値は処理されません！
