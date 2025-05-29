```
dither([T::Type,] img, alg::AbstractDither, args...; kwargs...)
```

アルゴリズム `alg` を使用して画像 `img` をディザリングします。

# 出力

戻り値の型が指定されていない場合、`dither` は入力画像の型をデフォルトとします。
