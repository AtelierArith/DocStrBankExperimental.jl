```
dither!([out,] img, alg::AbstractDither, args...; kwargs...)
```

アルゴリズム `alg` を使用して画像 `img` にディザリングを行います。

# 出力

`out` が指定されている場合、それはインプレースで変更されます。そうでない場合、`img` がインプレースで変更されます。
